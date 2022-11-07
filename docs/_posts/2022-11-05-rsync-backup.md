---
layout: post
title: "Rsync Backup"
toc: true
categories:
  - Tech
tags:
  - software
  - linux
date:   2022-11-05 6:01:50 PM
---

Clean up the notes of using `rsync` backing up/mirroring a directory tree of files 
from one machine to another machine. I will review `rsync` syntax and some 
important options from [rsync documentation](#refb). The demo script was referenced 
from [Use rsync to back up a directory tree of files](#refa) and modified for 
**auto-login** with no password prompts by configuring SSH so that an automated 
backup task can be scheduled using `cron`. 

## Introduction

rsync is a utility for efficiently transferring and synchronizing files between 
a computer and a storage drive and across networked computers by comparing the 
modification times and sizes of files. It is commonly found on Unix-like 
operating systems and is under the GPL-3.0-or-later license.

## Syntax 

`rsync` can be launched both locally, remotely or via rsync daemon, but I will 
only demonstate execute `rsync` remotely between two machines at the command 
prompt: 

~~~console
$ #Pull:
$ rsync [OPTION...] [USER@]HOST:SRC... [DEST]
$ #Push:
$ rsync [OPTION...] SRC... [USER@]HOST:DEST
~~~

Connecting directly to a remote `rsync-daemon` through TCP port 873, does not 
reuqire a remote shell as the transport. This obviously needs the `rsync-daemon` 
to be running on the remote system. However, it's possible to use `rsync-daemon` 
features via a remote shell connection, by explicitly set the remote shell 
program on the command-line with the **--rsh=COMMAND** option. 

### Options

Rsync accepts both long (double-dash + word) and short (single-dash + letter) 
options. Some useful options are described below. Some options only have a 
long variant, not a short.

When specifying a parameter, you can either use the form **--option=param**, 
**--option param**, **-o=param**, **-o param**, or **-oparam** (the latter three 
choices assume that your option has a short variant).

The parameter may need to be quoted in some manner for it to survive the shell's 
command-line parsing. Also keep in mind that a leading tilde (**~**) in a 
pathname is substituted by your shell, so make sure that you separate the option 
name from the pathname using a space if you want the local shell to expand it.

| Option | Description |
| ------ | ----------- |
| -\-archive, -a | archive mode to preserve almost everything: file permissions, ownership, timestamp, etc. |
| -\-compress-level=NUM, --zl=NUM | For zlib & zlibx compression the valid values are 0-9, default 6. 0 implies no compression. |
| --exclude-from=FILE | read exclude patterns from FILE, If a line begins with "- " (dash, space) or "+ " (plus, space), then the type of rule is being explicitly specified as an exclude or an include (respectively). |
| --exclude=PATTERN | exclude files matching PATTERN |
| -\-rsh=COMMAND, -e | specify the remote shell to use. |
| -\-relative, -R | use relative path names, insert a dot and a slash into the source path to limit the amount of path information that is sent as implied directories. | 
| -\-dry-run, -n | perform a trial run with no changes made and produce mostly the same output as a real run. |
| -\-update, -u | skip files that are newer on the receiver. |
| -\-verbose, -v | increase verbosity, A single -v will give you information about what files are being transferred and a brief summary at the end. Two -v options will give you information on what files are being skipped and slightly more information at the end. More than two -v options is for debugging rsync. |
| -\-compress, -z | compress file data during the transfer, which reduces the amount of data being transmitted. useful over a slow connection. |
| -\-log-file=FILE | log what we're doing to the specified FILE


### Configure `ssh` for auto login

**-\-rsh** option allows you to choose an alternative remote shell program to 
use for communication between the local and remote copies of rsync. Typically, 
**`rsync`** is configured to use **`ssh`** by default, but you may prefer to 
use **`rsh`** on a local network.

**NOTE**: **`rsh`** is convenient, but it has some serious security shortcomings. 
Like **`telnet`** and **`ftp`**, **`rsh`** traffic is passed as clear text. If 
you connect to a server via rlogin and su to the root account, you're sharing 
that root password with anyone who happens to be listening in on your traffic.

In this section, we are configuring automatic **`ssh`** login without password 
so that the backup script could be launched by the schedule. A good practice 
of **`ssh`** usage is that each private key corresponds to a single *identity* 
for a given user per host.  First, we generate a authentication key pair at 
the host machine: 

~~~console
$ cd ~/.ssh
$ ssh-keygen -t rsa -b 4096 -f host_rsa_keypair_name
~~~

The command will create a pair of key with specified name: **host_rsa_keypair_name** 
and **host_rsa_keypair_name.pub**. Copy and paste the public key to the 
**~/.ssh/authorized_keys** file at the **destination** machine(s). 

Then, configure **~/.ssh/config** at the source machine to send only the right 
key and change the file's permission to **700**: 

~~~console
$ cat ~/.ssh/config
Host dest_name
    HostName dest.IP.address
    User 
    IdentityFile ~/.ssh/host_rsa_keypair_name
    IdentitiesOnly yes

$ chmod 700 ~/.ssh/config
$ ls -alh ~/.ssh/config
-rwx------ 1 root root 230 Oct 29 21:12 config
~~~

**NOTE**: Running rsync as root is dangerous. Consider creating a special "rsync" 
user and run rsync as this user. The main complication when doing this is that 
the rsync user must have sufficient permissions to read and write all the files 
that rsync will be accessing on both machines. This might require a long detour 
in assigning group permissions and such, but is much more secure than running 
rsync as root. 

Now, you can use **`ssh`** or **`rlogin`** test to see if you can establish 
a SSH connection without password prompts, Press Ctrl-D to log out: 

~~~console
$ ssh dest_name # or rlogin dest_name
Linux dest_name2.6.17.14ReadyNAS #1 Wed Sep 22 04:42:09 PDT 2010 padre unknown
$ logout
Connection to dest_name closed.
~~~


## Demo of rsync backup 

In the following example we demonstrate how to use **`rsync`** to back up a tmp 
directory tree from a local machine to a remote machine.  Then re-run the script, 
as needed, to keep the two machines "in sync."  It only copies new or changed 
files and ignores identical files.

~~~console
#!/bin/sh
# Simple rsync "driver" script.  (Uses SSH as the transport layer.)
# chmod 700 rsync_demo.sh
# Run rsync_demo.sh by typing ./rsync_demo.sh
# http://www.scrounge.org/linux/rsync.html

# allows only you to write data, but anyone can read data. 
umask 022

# Destination host machine name
DEST="dest_name"

# User that rsync will connect as
# Are you sure that you want to run as root, though?
USER="root"

# Directory to copy from on the source machine. path before "./" is not backed up
BACKDIR="/data/./tmp/"

# Directory to copy to on the destination machine.
DESTDIR="/data/"

# exclude-from=file
# excludes file - Contains wildcard patterns of files to exclude.
# i.e., *~, *.bak, etc.  One "pattern" per line.
EXCLUDES=/data/tmp/excl_demo

# --log-file=FILE
FILE=/var/log/backup/demo_rsync.log
NAME=${FILE%.*}
EXT=${FILE#*.}
DATE=`date +%y-%m-%d_%H-%M-%S`
LOG=${NAME}_${DATE}.${EXT}
echo $LOG

# For testing.  Only displays what rsync *would* do and does no actual copying.
#OPTS="-n -vv -u -a -R -z --rsh=ssh --exclude-from=$EXCLUDES --stats --progress"

# Does copy, but still gives a verbose display of what it is doing
#OPTS="-v -u -a -R -z --rsh=ssh --exclude-from=$EXCLUDES --stats"

# Copies and does no display at all. Save the log file 
#OPTS="--update --archive --relative --compress --rsh=ssh --exclude-from=$EXCLUDES --quiet --log-file=$LOG"

# May be needed if run by cron?
export PATH=$PATH:/bin:/usr/bin:/usr/local/bin

# Only run rsync if $DEST responds.
VAR=`ssh -q $DEST exit; echo $?`
if [ $VAR -eq 0 ]; then
        rsync $OPTS $BACKDIR $USER@$DEST:$DESTDIR
else
        echo "Cannot connect to $DEST."
fi
~~~

If **`ssh`** command exits successfully, it will always returns **`0`**. You 
can simply check **`$?`**. 

In order to let the script to **`rsync`** some real file, you can create dummy 
file with: 

~~~console
$ cd /data/tmp
$ dd if=/dev/zero of=foo.img bs=1M count=100
$ dd if=/dev/urandom of=foo.img bs=1M count=100
~~~

**/dev/zero** will create a 100Mb file full of zeros, which compresses really 
well. **/dev/urandom** to create random files with substantial size after compression. 
The dummy file was included in the excl_demo file, recalling that "**\+** " 
(plus and space) indicates inclusion. 

~~~console
$ touch /data/tmp/excl_demo
$ cat /data/tmp/excl_demo
+ foo.img
~~~

The execution of the scripts look likes this: 

~~~console
$ ./rsync_demo.sh
/var/log/backup/demo_rsync_22-11-06_11-51-52.log
$ cat /var/log/backup/demo_rsync_22-11-06_11-51-52.log
2022/11/06 11:52:12 [11978] building file list
2022/11/06 11:52:12 [11978] sent 86 bytes  received 21 bytes  total size 104857600
~~~

### Schedule backup scripts with **`cron`**

The easiest way to launch **`rsync`** backup scripts on schedule in the background 
is to use **`cron`** job scheduler. To do this, you simply need to add the schedule 
of the **`rsync`** backup scripts to the **/etc/crontab* file:


~~~console
$ cat /etc/crontab
# /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file
# and files in /etc/cron.d. These files also have username fields,
# that none of the other crontabs do.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow user  command
00 24   * * 7   root    ~/bin/rsync_demo.sh
#
~~~

The abbreviation of schedule format from the comments in the **`crontab`** file 
means the following:

| Option | Description |
| ------ | ----------- |
| m  | minute |
| h  | hour |
| dom | day of month |
| mon | month |
| dow | day of week |
| command | the command to execute |

Hence, my schedule command means that rsync_demo.sh will run at **24:00 on Friday weekly**.

**NOTE**: host computers must be on during the scheduled time to execute 
the **`rsync`** backup. **`cron`** will not run missed jobs. To run missed 
jobs, look at **`anacron`**[^1]. 

[^1]: Unlike **`cron`** , it does not assume that the machine is running continuously. Hence, it can be used on machines that aren't running 24 hours a day, to control regular jobs as daily, weekly, and monthly jobs.

## References

+ Use rsync to back up a directory tree of files.[http://www.scrounge.org/linux/rsync.html](http://www.scrounge.org/linux/rsync.html){: target="_blank"}.
{: id="refa"} 
+ rsync documentation. [https://download.samba.org/pub/rsync/rsync.1](https://download.samba.org/pub/rsync/rsync.1){: target="_blank"}.
{: #refb}