---
layout: post
title: "Robocopy Backup"
toc: true
categories:
  - Tech
tags:
  - robocopy
  - backup
  - windows
date:   2022-08-12 4:02:02 PM
---

Reviewed some often used syntax of Robocopy, examples were given on how to select 
files, log outputs, and save/load robocopy backup jobs. Finally, documented the 
steps of setting schedule for backup jobs under windows system. 

## Introduction

**Robocopy**, (Robust File Copy), is a command-line directory and/or file 
replication command for Microsoft Windows. Robocopy functionally replaces 
built-in Windows **copy** and **Xcopy**, with capabilities above and beyond. 
It is intended for consistent copying or mirroring of directories wherever 
the computer has access, including local drives, removable drives, 
Local Area Network, remote servers, and in the process guarantees that 
all file properties and permissions stay integral.

## Syntax

To run Robocopy, use the following syntax at the command prompt: 

~~~console
C:\Users\JohnDoe>robocopy source destination [file [file] ... ] [parameters]
~~~

The following table defines these syntax elements 

| Variable    | Meaning | Comments |
| ----------- | ------- | ---------------------------------------------------- |
| source      | specifies source folder | You can use drive:\path or \\server\share\path |
| destination | specifies the destination folder | You can use drive:\path or \\server\share\path |
| file        | Files to process | Wildcard characters are supported (__*__ match any sequence of characters, __?__ match a single character) |
| options     | Command-line options including copy, file, retry, logging, and job options | Available options are described below |

**Tip** To view brief usage instrucitons at the command prompt, run "**ROBOCOPY /?**". 

### Copy Options

Some useful options were tabulated below: 

| Option | Description |
| ------ | ----------- |
| /s |  Copies subdirectories. This option automatically excludes empty directories.  |
| /e | 	Copies subdirectories. This option automatically includes empty directories. |
| /z | 	Copies files in restartable mode. In restartable mode, should a file copy be interrupted, Robocopy can pick up where it left off rather than recopying the entire file. |
| /b | Copies files in backup mode. Backup mode allows Robocopy to override file and folder permission settings (ACLs, i.e., Access-control lists). This allows you to copy files you might otherwise not have access to, assuming it's being run under an account with sufficient privileges. |
|/zb | Copies files in restartable mode. If file access is denied, switches to backup mode. |
| /copy: | Specifies which file properties to copy. The valid values for this option are: {::nomarkdown}<ul><li>D - Data</li><li>A - Attributes</li><li>T - Time stamps</li><li>S - NTFS access control list (ACL)</li><li>O - Owner information</li><li>U - Auditing information</li></ul> {:/} The default value for this option is DAT (data, attributes, and time stamps).|
| /purge | Deletes destination files and directories that no longer exist in the source. |
| /mov | Moves files and deletes them from the source after they are copied.  |
| /mir | Mirrors a directory tree (equivalent to running both /e and /purge). |
| /mt[:n] | Creates multi-threaded copies with n threads. n must be an integer be| tween 1 and 128. The default value for n is 8. For better performance, redirect your output using /log option.|
|/compress | Requests network compression during file transfer, if applicable.|

For example, Mirror the source folder 'C:\Users\John' to destination folder 
'F:\TheBackup' excluding empty subfolder: 

~~~console
C:\Users\JohnDoe>Robocopy 'C:\Users\John' 'F:\TheBackup' /s /copy:DAT /mir
~~~

**NOTE** You must have the Backup Files and Restore Files privileges to copy 
files in Backup Mode using /**b** or /**zb**. 

**NOTE** Backup mode copies are not restartable, but they enable you to copy 
some files as a Backup Operator that you would not be able to copy as a normal user. 

**NOTE** If you use /**z**, /**b**, or /**zb**, this can decrease Robocopy 
performance and throughput significantly, as these options involve extra overhead. 
These options are therefore only recommended when experience indicates you 
really need them. 

### File selection options

Selected useful options: 

| Option | Description |
| ------ | ----------- |
| /xa:[RASHCNETO] | Excludes files for which any of the specified attributes are set. The valid values for this option are: {::nomarkdown}<ul><li>R - Read only</li><li>A - Archive</li><li>S - System</li><li>H - Hidden</li><li>C - Compressed</li><li>N - Not content indexed</li><li>E - Encrypted</li><li>T - Temporary</li><li>O - Offline</li></ul> {:/} |
| /xf <filename> | Excludes files that match the specified names or paths. Wildcard characters (\* and \?) are supported.|
| /xd <dir> | Excludes directories that match the specified names and paths.|
| /xj | Excludes junction points, which are normally included by default. |
| /xjd | Excludes junction points for directories. |
| /fft | assume FAT File Times (2-second granularity). |
| a | b |

An NTFS **junction point** is a symbolic link to a directory that acts as an 
alias of that directory.  In Windows Explorer, a junction point looks like a 
folder with a shortcut icon in the bottom left corner. Don’t forget /**xj** to 
exlcude the junction points, when you backup a Windows user profile. Or else 
it will run forever, because it enters an infinite loop. 

/**fft** is important when backing up to a NAS based on LINUX. If you leave out 
this parameter it will keep copying the files to you NAS, even though they are 
already present. 

For example, Mirror backup, excluding system/hidden files, folder 'AppData' and 
all junction points for directories:

~~~console
C:\Users\JohnDoe>Robocopy 'C:\Users\John' 'F:\TheBackup' /mir /xa:SH /xd AppData /xjd
~~~

### Retry options

| Option | Description |
| ------ | ----------- |
| /r:<n> | Specifies the number of retries on failed copies. The default value of n is 1,000,000 (one million retries). |
| /w:<n> | Specifies the wait time between retries, in seconds. The default value of n is 30 (wait time 30 seconds). |

For example, same task with **5** retries and **15** seconds wait time between 
each retry: 

~~~console
C:\Users\JohnDoe>Robocopy 'C:\Users\John' 'F:\TheBackup' /mir /xa:SH /xd AppData /xjd /r:5 /w:15
~~~

| a | b |
| a | b |
| a | b |

### Logging options

During a run, Robocopy creates an Output Log that comprises a Job Header detailing
the command line arguments used for the job, a list of files and directories processed
during the job, and a Job Summary that shows totals copied, etc. By default, Output
Log is written to the command prompt. This output can be redirected to a file, either by
using the standard command-line operators (> or \>\>), or by using one of the commandline
options: /**log** or /**log+**. 

/**tee** in conjunction with /**log** or /**log+** options causes Robocopy to 
log its output to both the command prompt (for visual progress monitoring) and 
the specified file (for a permanent record of the Robocopy run).

| Option | Description |
| ------ | ----------- |
| /l | Specifies that files are to be listed only (and not copied, deleted, or time stamped). |
| /x | Reports all extra files, not just those that are selected. |
| /v | Produces verbose output, and shows all skipped files. |
| /np | Specifies that the progress of the copying operation (the number of files or directories copied so far) will not be displayed. |
| /eta | Shows the estimated time of arrival (ETA) of the copied files.|
| /log:<logfile> | Writes the status output to the log file (overwrites the existing log file). |
| /log+:<logfile> | Writes the status output to the log file (appends the output to the existing log file). |
| /tee | Writes the status output to the console window, and to the log file. |

By default, the only Extra files reported are those that match files specified 
for copying on the command line. In most cases, this is more efficient. 
For example, if you are refreshing .**cpp** files, you probably do not need 
information about .**txt** files in the destination. If you want a list of all 
Extra files in the destination, regardless of their type, use the /**x** switch.


No output is produced for skipped files. To obtain a verbose listing that shows all
source files specified for copying on the command line, including skipped files, 
use the /**v** switch.

Robocopy provides copy progress information (% copied) by default. You can use 
the /**np** switch to suppress the display of progress information. This can be 
useful when output is redirected to a file.

To see the start time of each file copy and the estimated time of completion based on
the observed throughput of previous copies, use the /**eta** switch. Times are 
displayed after the file name in the format HH:MM –> HH:MM (start –> finish).

Finally, to obtain only a list of the files that would be copied (without 
actually copying them), use the /**l**  switch.

~~~console
PS C:\> Robocopy.exe 'c:\files\src\' 'c:\files\dest\' *.txt /v /l

-------------------------------------------------------------------------------
   ROBOCOPY     ::     Robust File Copy for Windows
-------------------------------------------------------------------------------

  Started : Friday, August 12, 2022 10:35:41 AM
   Source : c:\files\src\
     Dest : c:\files\dest\

    Files : *.txt

  Options : /V /L /DCOPY:DA /COPY:DAT /R:1000000 /W:30

------------------------------------------------------------------------------

                           2    c:\files\tmp\src\
            New File              273168        doc.txt
            New File              623678        readme.txt

------------------------------------------------------------------------------

               Total    Copied   Skipped  Mismatch    FAILED    Extras
    Dirs :         1         0         1         0         0         0
   Files :         2         2         0         0         0         0
   Bytes :   875.8 k   875.8 k         0         0         0         0
   Times :   0:00:00   0:00:00                       0:00:00   0:00:00
   Ended : Friday, August 12, 2022 10:35:41 AM

PS C:\>
PS C:\> Robocopy.exe 'c:\files\tmp\src\' 'c:\files\tmp\dest\' *.cpp  /x /eta

-------------------------------------------------------------------------------
   ROBOCOPY     ::     Robust File Copy for Windows
-------------------------------------------------------------------------------

  Started : Friday, August 12, 2022 10:45:11 AM
   Source : c:\files\tmp\src\
     Dest : c:\files\tmp\dest\

    Files : *.cpp

  Options : /X /DCOPY:DA /COPY:DAT /ETA /R:1000000 /W:30

------------------------------------------------------------------------------

                           3    c:\files\tmp\src\
          *EXTRA File             273168        doc.txt
          *EXTRA File             623678        readme.txt
100%        New File                 103        library1.cpp
100%        New File                 223        library2.cpp    10:45 -> 10:45
100%        New File                  94        main.cpp        10:45 -> 10:45

------------------------------------------------------------------------------

               Total    Copied   Skipped  Mismatch    FAILED    Extras
    Dirs :         1         0         1         0         0         0
   Files :         3         3         0         0         0         2
   Bytes :       420       420         0         0         0   875.8 k
   Times :   0:00:00   0:00:00                       0:00:00   0:00:00


   Speed :               30000 Bytes/sec.
   Speed :               1.716 MegaBytes/min.
   Ended : Friday, August 12, 2022 10:45:11 AM

PS C:\>
~~~

### Job options

Given the large number of command-line options available, it is easy to create
Robocopy commands that are extremely long, and unwieldy to manipulate. Using
Robocopy Job Files can greatly simplify matters.

Robocopy Job Files are simple text files containing one Robocopy parameter per 
line, that you can create, view, and edit manually using a text editor, or, 
more simply, you can use Robocopy itself for all of these tasks.

| Option | Description |
| ------ | ----------- |
| /job:<jobname> | Specifies that parameters are to be derived from the named job file. To run /job:jobname, you must first run the /save:jobname parameter to create the job file. |
| /save:<jobname> | Specifies that parameters are to be saved to the named job file. This must be ran before running /job:jobname. All copy, retry, and logging options must be specified before this parameter. |
| /quit | 	Quits after processing command line (to view parameters).|
| /nosd | Indicates that no source directory is specified. |
| /nodd	| Indicates that no destination directory is specified. |
| /if   | Includes the specified files. |

To encapsulate this command in a Robocopy Job File without running the job: 

~~~console
PS C:\> Robocopy.exe 'c:\files\src\' 'c:\files\dest\' *.txt /v /x /save:rbackup /quit
~~~

This creates a Robocopy Job File named **rback.rcj** in the current directory 
that encapsulates all the Robocopy parameters you specified prior to the 
/**save** switch.

**NOTE** /**save** is actioned as soon as it is encountered on the command line. Any
arguments on the command line after /**save** will not be saved.

To run the resulting Robocopy Job File at a later date, assuming the same working
directory, the following command would suffice:

~~~console
PS C:\> Robocopy.exe /job:rbackup
~~~

**NOTE** Both /**save** and /**job** expect the file to have a .RCJ suffix, and 
append a .RCJ suffix to the provided filename if it does not have one.

**NOTE** /**save** writes to the specified file immediately, with no warning if the
target file already exists. Care should be taken that you do not overwrite existing
files when using /**save** to create a new Robocopy Job File.

To edit a job file, you can use /**job** /**save** and /**quit** together as follows:

~~~console
PS C:\> Robocopy.exe /job:rbackup /xf doc.txt /save:rbackup /quit
~~~

This loads the named job, adds parameters to exclude doc.txt files from the job, 
and updates it on disk. 

It is sometimes useful to create Robocopy Job Files that can be used as templates for
similar types of copies, and for this purpose it is perfectly valid to save a job file
without specifying a source directory or destination directory or both. Such a job file
**cannot** be run on its own, of course, unless the source and destination directories are
specified at run time.

~~~console
PS C:\> Robocopy.exe /nosd /nodd *.c* *.h* readme.txt doc.txt /save:rb_files /quit
~~~

Such a job structure would enable you to back up your projects simply and
consistently using brief commands like the following:

~~~console
PS C:\> Robocopy.exe /job:rb_files /job:rbackup
~~~

**NOTE** The order of the two job files does not matter, but one job file 
(rbackup in this example)  must include both source and destination directories. 

This is just an introduction to Robocopy Job Files with simple and straightforward
examples, but their flexibility an open-endedness enables large and complicated jobs to
be created and managed with ease.

### Exit (return) codes

The return code from Robocopy is a bit map, defined as follows:

| Value | Meaning If Set |
| ------ | ----------- |
| 0 | No files were copied. No failure was encountered. No files were mismatched. The files already exist in the destination directory; therefore, the copy operation was skipped.b |
| 1 | All files were copied successfully. |
| 2 | There are some additional files in the destination directory that are not present in the source directory. No files were copied. |
| 3 | Some files were copied. Additional files were present. No failure was encountered. |
| 5 | Some files were copied. Some files were mismatched. No failure was encountered. |
| 6 | Additional files and mismatched files exist. No files were copied and no failures were encountered. This means that the files already exist in the destination directory. |
| 7 | Files were copied, a file mismatch was present, and additional files were present. |
| 8 | Some files or directories could not be copied (copy errors occurred and the retry limit was exceeded). Check these errors further. |


You can use this information in a batch file to report the most serious anomalies, as
follows:

~~~console
if errorlevel 16 echo ***FATAL ERROR*** & goto end
if errorlevel 8 echo **FAILED COPIES**  & goto end
if errorlevel 4 echo *MISMATCHES*       & goto end
if errorlevel 2 echo EXTRA FILES        & goto end
if errorlevel 1 echo Copy successful    & goto end
if errorlevel 0 echo --no change--      & goto end
:end
~~~

## Topics

### Using Robocopy Within a UNIX Shell

You can specify all Robocopy switches in UNIX style (for example, **-ETA** instead 
of **/ETA**). You can also specify source and destination directory paths using 
the UNIX delimiter (**/**), rather than the native Windows delimiter (**\\**).

The only restriction is that any argument that begins with a UNIX slash mark 
(**/**) is treated as a switch if the argument contains only a **single** slash 
mark (**/**). In other words, /dir is treated as a switch; but 
//server/share/dir and /download/test are treated as paths.

This avoids any possible confusion between switches and single-level paths
subordinate to the root of a drive. To specify a directory as an argument, 
you must use an alternate expression for its path, such as X:/dir or //server/C$/dir.

### Scheduling Robocopy Jobs

You can configure the **Task Scheduler** service from a user account. Once the user
account has been granted appropriate access to source and destination servers, you
can schedule Robocopy jobs to copy files between them.

To configure the Schedule service to log on as a user account: 

 + 1. In Control Panel, find **Task Scheduler**, Click menu **action**, then **Create Basic Task**. 
 + 2. In the Dialog box, give the task a name and desscription, then choose the frequency of the task, e.g., Weekly. 
 + 3. In Action of the task, choose the robocopy.bat script. 