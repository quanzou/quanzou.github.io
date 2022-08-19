---
layout: post
title: "Blojsom Weblog How-to "
toc: true
categories:
  - Tech
tags:
  - hardware
  - linux
date:   2007-08-08
---

[**`Blojsom`**](https://github.com/timothystone/blojsom){:target="_blank"} is a 
Java-based, full-featured, multi-blog, multi-user software package. Weblog 
Server based on the popular open source project **`Blojsom`** with an easy-to-use 
interface, makes publishing a weblog as simple as checking a box in Server Admin 
preferences. **`Blojsom`** Weblog Server provides users with calendar-based 
navigation and customizable themes and users can post entries using the built 
in Web-based functionality or with weblog clients that support XML-RPC or 
the Atom API.

Since I have struggled to setup everything working out for Blojsom under my 
system, I felt that I am obligated to write down some tips I had during 
my installation.

## Requirements

You have to meet several requirements in advance to make the current version of 
**`Blojsom 3.2`** work, although you can find a step-by-step of installation 
on blojsom website. And I found this in a hard way, search the bug reports over 
google for weeks. Please note that everything I write down is mainly concerning 
about **`SuSE 9.1`** box. The combination I choose is **`MySQL`** + **`Apache2`** 
+ **`Tomcat`** + **`Blojsom 3.2`**.

### TomCat

[**`Tomcat`**](https://tomcat.apache.org/){:target="_blank"} is the servlet 
container that is used in the official Reference Implementation for the Java 
Servlet and JavaServer Pages technologies. The Java Servlet and JavaServer 
Pages specifications are developed by Sun under the Java Community Process.

You will need at least **`Tomcat`** version 5.0.xx up to make **`Blojsom`**] 3.2 
work! There are several ways to check the version number you are using: 

 + go the this url **`http://localhost:8080/manager/html/list`** should display 
 the Tomcat documentation if Tomcat has already installed properly. The version 
 number will be in the bottom left hand. 

 + the version number is mentioned in **`/srv/www/tomcat/demoserver/webapps/ROOT/RELEASE-NOTES.txt`**. 
 
 + check the log file **`$TOMCAT_HOME/logs/catalina.out`**, the first few lines 
 show the version number. 
 
I am pretty sure there must be other ways to find it out, but the ones above 
is enough. The version number I am having is **`5.0.19`**.

In addition, you will need build **`JK Connector 1.2.15`**, to let TomCat and 
Apache talk to each other. In order to build JK Connector, **`httpd-devel`** 
package containing **`apxs2`** must be installed, where **`apxs2`** stands for 
Apache2 Extension Tools. After you download and unpack it, and excute the 
following commands to builds the connector: 

~~~bash
$ cd path-where-you-put-it/jk/native/
$ ./configure --with-apxs2=/usr/sbin/apxs2
$ make
$ cp path-where-you-put-it/jk/native/apache-2.0/mod_jk.so /usr/lib/apach2/mod_jk.so
~~~

Finally, put the following lines in the **``$TOMCAT_HOME/conf/server.xml`**:

~~~bash
<Server port="8005" shutdown="SHUTDOWN" debug="0">
<Listener className="org.apache.jk.config.ApacheConfig" modJk="/usr/lib/apache2/mod_jk.so" />
~~~

### MySQL

The reason I choose **`MySQL`** as the database server is due to its reliability 
and speed. Oracle will probably crash my old slow laptop by consuming all the 
memory, and I heard that PostgreSQL has speed limitations, but I haven't checked 
that out.

Unfortunately, **`SuSE 9.x`** doesn't come with **`MySQL 5.0.xx`**, which is 
required by **`Blojsom 3.2`**. Blojsom 3.2 use UTF-8 code, and **`MySQL 4.0.xx`** 
doesn't support UTF-8 character set. You can either confirm this by the following
command: 

~~~bash
$ mysql -u zoublog -p
Enter password:
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 95
Server version: 5.1.63-0+squeeze1 (Debian)

Copyright (c) 2000, 2011, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> show character set;
+----------+-----------------------------+---------------------+--------+
| Charset  | Description                 | Default collation   | Maxlen |
+----------+-----------------------------+---------------------+--------+
| big5     | Big5 Traditional Chinese    | big5_chinese_ci     |      2 |
| dec8     | DEC West European           | dec8_swedish_ci     |      1 |
| cp850    | DOS West European           | cp850_general_ci    |      1 |
| hp8      | HP West European            | hp8_english_ci      |      1 |
| koi8r    | KOI8-R Relcom Russian       | koi8r_general_ci    |      1 |
| latin1   | cp1252 West European        | latin1_swedish_ci   |      1 |
| latin2   | ISO 8859-2 Central European | latin2_general_ci   |      1 |
| swe7     | 7bit Swedish                | swe7_swedish_ci     |      1 |
| ascii    | US ASCII                    | ascii_general_ci    |      1 |
| gb2312   | GB2312 Simplified Chinese   | gb2312_chinese_ci   |      2 |

...

mysql> 
~~~

or you can tell your version by these commands. 

~~~bash 
$ mysql -V
mysql  Ver 14.14 Distrib 5.1.63, for debian-linux-gnu (i486) using readline 6.1
$
$ /usr/bin/mysqladmin  --version
/usr/bin/mysqladmin  Ver 8.42 Distrib 5.1.63, for debian-linux-gnu on i486
~~~ 

If it's below **5.0.xx** or doesn't have character set support, I suggest you 
to grab the latest source code, and do a customized compilation for your system. 
To do this you need to go through the reference online, which will not be 
covered in this documents.

To let **`TomCat`** control **`MySQL`** over **`Java`**, you need **`mysql connector 3.1.14`** 
downloaded, and put them into **`$TOMCAT_HOME/common/lib/mysql-connector-java-3.1.14-bin.jar`** .

## Configurations

### Security

First thing first, you need to set a password for the MySQL root USER! To do so, 
start the server, then set the root password: 

~~~bash
$ sudo /etc/init.d/mysql start
$ /usr/local/bin/mysqladmin -u root password 'new-password'
~~~

I strongly suggest that you run mysql daemon from a user account, for example 
**`mysql`**. You can do the following from system root (do NOT confuse with the 
mysql root): 

~~~bash
$ sudo groupadd mysql
$ useradd -g mysql mysql
~~~

You can manually start the MySQL daemon from mysql account with: 

~~~bash
$ /usr/bin/mysqld_safe
~~~

Under the **`Debian`** version **`6.0.4 squeeze`**, the symql daemon has already 
ran under safe mode from user account mysql. 

It will be also nice to run **`TomCat`** from a user account, like tomcat. You can 
create .bashrc config file under home: **`/usr/share/tomcat/.bashrc`**.

~~~bash
export PATH=$HOME/bin:$HOME/usr/bin:$PATH
export PATH=/usr/lib/SunJava2-1.4.2/bin:$PATH
# Tomcat and Java environment variable
TOMCAT_HOME=/usr/share/tomcat ; export TOMCAT_HOME
JAVA_HOME=/usr/lib/SunJava2-1.4.2 ; export JAVA_HOME
~~~

You are really supposed to launch and/or stop **`TomCat`** from tomcat account, 
by: 
~~~bash
$ $TOMCAT_HOME/bin/startup.sh
$  
$ $TOMCAT_HOME/bin/shutdown.sh
~~~

You will also need to configure Admin and manager Web Application: edit file 
**`CATALINA_BASE/conf/tomcat-users.xml`** add the following line as examples:

~~~bash
<role name="admin"/>
<role name="manager"/>
<user name="admin" password="deep_dark_secret" roles="admin"/>
<user name="manager" password="deep_dark_secret" roles="manager"/>
~~~

Now, you can have more control of TomCat over Http:

**`http://localhost:8080/`**

**`http://192.168.2.117:8080/host-manager/html`**

![tomcat_admin](https://bn1303files.storage.live.com/y4mDTblQ7zgUYzGMuJRpPTfZYHN-8UVAoNCW1_y5YeMLjKe9G7oEPPq_MDpDpRjtgt-dn61JxvMepzvTLLyvk-eJaTTclSQTheOGTaVsIornmDPUlNwX--FxQOcu7Vl8rJ-svdduS4it_3e7TXN0kXpK3jd9V7GW9TS65dpSOgYH9SIjwcM3Ke70ScqheT9oHyj?width=973&height=841&cropmode=none){: width="973" height="841"}


### Apache2

create **`/etc/apache2/httpd.tomcat.conf`**, as the following example:

~~~bash
Include /usr/share/tomcat/conf/auto/mod_jk.conf

# Where to find workers.properties
JkWorkersFile /usr/share/tomcat/conf/workers.properties

# Where to put jk logs
JkLogFile /var/log/apache2/mod_jk.log

# Set the jk log level [debug/error/info]
JkLogLevel info

# Select the log format
JkLogStampFormat "[%a %b %d %H:%M:%S %Y] "

# JkOptions indicate to send SSL KEY SIZE,
JkOptions +ForwardKeySize +ForwardURICompat -ForwardDirectories

# JkRequestLogFormat set the request format
JkRequestLogFormat "%w %V %T"
~~~

in file **`/etc/sysconfig/apache2`** add the following lines:


~~~bash
APACHE_CONF_INCLUDE_FILES="httpd.tomcat.conf"
APACHE_CONF_INCLUDE_DIRS="/etc/apache2/tomcat"
~~~

you can create 2 conf files under **`/etc/apach2/tomcat/`**: 
**`vhost.tomcat-admin.conf`** and **`vhost.tomcat-blojsom.conf`** to setup the 
**`DocumentRoot`** and directory for virtual host. This will make your migration 
or upgrade lot easier. You can create those conf files from **`vhost.template`**, 
but make sure to include the following lines in, respectively.

for **`vhost.tomcat-admin.conf`**, something like this:

~~~bash
<VirtualHost 192.168.1.2:8080>
ServerAdmin webmaster@neurosim.minidns.net
ServerName neurosim.minidns.net:8080
DocumentRoot /usr/share/tomcat/server/webapps/
ErrorLog /var/log/apache2/tomcat-admin-error_log
CustomLog /var/log/apache2/tomcat-admin-access_log combined
HostnameLookups Off
UseCanonicalName Off
ServerSignature On
<Directory "/usr/share/tomcat/server/webapps/">
Options Indexes FollowSymLinks
AllowOverride None
Order allow,deny
Allow from all
</Directory>
</VirtualHost>
~~~

for **`vhost.tomcat-blojsom.conf`**, something like this:

~~~bash
DocumentRoot /usr/share/tomcat/base/webapps/blojsom/
ErrorLog /var/log/apache2/tomcat-blojsom-error_log
CustomLog /var/log/apache2/tomcat-blojsom-access_log combined
<Directory "/usr/share/tomcat/base/webapps/blojsom/">
~~~

### Blojsom3.2

Now, we are getting down to the most exciting part.

#### Create user account

Create a new user in MySQL with full permissions for your given host.

~~~bash
$ mysql -u root -p
password: *****
mysql> create database blojsom;
mysql> grant all on blojsom.* to blojsom@'%' identified by 'somepassword';
mysql> grant all on blojsom.* to blojsom@localhost identified by 'somepassword';
mysql> use blojsom;
mysql> flush privileges;
mysql> quit
~~~

#### Setup encoding attribute

Open **`%TOMCAT_HOME%/conf/server.xml`** file and check out the settings for 
various defined elements. Set the URIEncoding attribute to **`UTF-8`**, which 
is the character encoding format blojsom uses for encoding links. For example:

~~~bash
<Connector port="8080"
maxThreads="150" minSpareThreads="25" maxSpareThreads="75"
enableLookups="false" redirectPort="8443" acceptCount="100"
debug="0" connectionTimeout="20000"
disableUploadTimeout="true" URIEncoding="UTF-8"/>
~~~

#### Download Blojsom

Download the **`blojsom 3.2`** blojsom.war file. Create a web application 
directory for the blojsom 3.2 WAR file in **`%TOMCAT_HOME%/webapps`**, Copy 
the blojsom.war file into the **`%TOMCAT_HOME%/webapps/blojsom`** directory. 
Unpack the blojsom.war file and delete it afterward: 

~~~bash
$ mkdir %TOMCAT_HOME%/webapps/blojsom
$ cp blojsom.war %TOMCAT_HOME%/webapps/blojsom
$ jar xvf blojsom.war
$ rm blojsom.war
~~~ 

#### Add **`mysql`** user account

Edit **`%TOMCAT_HOME%/webapps/blojsom/WEB-INF/classes/blojsom-helper-beans-include.xml`** 
and change only the values for the username and password for **`blojsom`** database 
to the username and password you created earlier.

~~~bash
<bean id="dataSource" class="org.apache.commons.dbcp.BasicDataSource" destroy-method="close">
<property name="driverClassName" value="com.mysql.jdbc.Driver"/>
<property name="url" value="jdbc:mysql://localhost/blojsom?autoReconnect=true&useUnicode=true&characterEncoding=utf-8"/>
<property name="username" value="blojsom"/>
<property name="password" value="somepassword"/>
</bean>
~~~

#### Run the blog webpage

Start Tomcat You may now access your blog at **`http://localhost:8080/blojsom/blog/default/`** 
You may access the administration console at **`http://localhost:8080/blojsom/blog/default/?flavor=admin`** 
The default user and password is default/default. Be sure to change the password 
immediately after logging in. You can change this under **Weblog Settings | Users`**.

![blojsom_mgnt](https://bn1303files.storage.live.com/y4mmb_HKx9vtbV1qWtdaMrmakWDieg5KgFpJnkhNW1sGUaPL2sjgzLAUBh7ubMcwpJEBTeb-ruiDf8mau4eYiR2EM7Rfwxj2-SW0XP7rECDJ5RNI0nXzcMIzsPVlaX_2BO0Y5uAT66YM5_QLO3uh-Cv_FZ_3UMaD2Q2cPS8W07j9ARscsi6V1colhNKcrKyzWFD?width=1140&height=672&cropmode=none){: width="1140" height="672"}
