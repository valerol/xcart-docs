---
lang: en
layout: article_with_sidebar
updated_at: '2018-03-14 17:04 +0400'
identifier: ref_080K3Qe7
title: How to Restore a Site from Backup
order: 130
published: false
---
Generally speaking, restoring a store from a backup copy is an inverse procedure to creating the backup copy. When restoring the store, you are expected to use the same tools that you used to create the backup copy. Similar to creating the backup, restoring does not cause any serious difficulties, but it yet requires the standard sequence of operations: restore the store files and then restore the database. One of the major rules to be observed is to restore data from the backup to a newly created directory within the WWW part of your hosting account. You must keep with this rule no matter whether you simply copy/move the store to a new location or replace an existing installation with the backup copy. After you have restored your store from the backup, you may need to adjust some configuration settings, including the values of the variables in the main configuration file config.php, paths to images, file permissions, etc.

The instructions below generally describe how to restore X-Cart files from a backup copy. Examples and notes are provided for UNIX- and Windows-based servers. Many of the listed operations can be carried out through your server/hosting control panel (if any).

## Restoring X-Cart files from a back-up:

1. Log in to your server or your hosting account.

2. Go to the directory that contains all your Internet projects (usually referred to as the WWW directory), and create a new directory where you will deploy the store from the backup.
  
  On a UNIX-based server, you can create the new directory using the following shell command.
  
   ```
   > mkdir xcart
   ```
  
  On a Windows-based server, you can create the new directory using the graphic user interface (GUI).
  
  As a result, you should get an empty directory that is accessible through the Internet.
  
3. Go to the directory that you have just created and upload the X-Cart files (or the archive with X-Cart files) onto the directory using FTP, SCP, your control panel or other suitable facility.

4. If you have the X-Cart files in an archive, extract them using the available utilities.
   
  On a Unix-based server, you can extract files from the archive using the following shell command.
    
   ```
    > tar -xfv <archive_name>
   ```
  OR
   ```
   > tar –xzvf <archive_name> # If the archive has file extension *.tar.gz, *.gz or *.zip
   ```
  OR
   ```
   > tar –xjvf <archive_name> # If the archive has file extension *.tbz.
   ```
  On a Windows-based server, you can extract the archive with one of the available file archive managers for Windows, including WinRAR, WinZIP, PKZip or 7Zip.

5. Check the X-Cart directory. It must contain the standard X-Cart file structure. If it only contains one directory with the X-Cart files, move its content to the current directory.

6. If necessary, edit the main X-Cart configuration file <X-Cart>/etc/config.php:

  * Locate the file config.php and open it for editing in your favorite plain text editor.
  * Set correct values for the following variables:
  
    ```
    [database_details]
    hostspec = "localhost"
    socket   = ""
    port     = ""
    database = "database"
    username = "username"
    password = "password"
    table_prefix = "xc_"
    ```
  and

    ```
    [host_details]
    http_host = "<HOST>"
    https_host = "<HOST>"
    web_dir = "/xcart"
    ```
   
7. Create a new database for the store using a database management system (DBMS) that you usually use to manage your MySQL databases.

  On a Unix-based server, you can create the new database using the following shell command.

   ```
   > mysql -h<sql_host> -u<sql_user> -p -e"create database <sql_db>;"
   ```
  If you connect to the database server through a non-typical port or socket, use the following command.

   ```
   > mysql -P<sql_port> -h<sql_host> -u<sql_user> -p -e"create database <sql_db>;"
   ```
  OR

   ```
   > mysql -S<sql_socket> -h<sql_host> -u<sql_user> -p -e"create database <sql_db>;"
   ```
  
  The system will ask you to to enter your password for the MySQL account. After the password is accepted, the system will create a new empty database for your store.
  {% note  info%}
  The name/address of the MySQL server, the name of the MySQL database, the username and the password for the MySQL account must be the same as the values of the respective variables in the X-Cart configuration file config.php.
  {% endnote %}
  
## Restoring Database from SQL Dump

When you restore a database from an SQL dump, the existing database tables get overwritten. We strongly recommend that you always back up the current store database before restoring data from an SQL dump as it allows you to avoid any possible data loss. Another critical issue here is that you can restore the database only if the SQL dump was created for the same X-Cart version.

The store administrator can restore the database either through the X-Cart Admin area or manually. If you decide to carry out this task manually, ensure that you have access to the respective tools and facilities, including different client implementations of the SSH protocol like OpenSSH or PuTTY, Telnet, phpMyAdmin, MySQL console, control panel of your hosting account, Remote Desktop client and other. In this case, the exact instructions on how to restore the database from the backup will depend on the utility you use.

The example below describes how you can restore the database using terminal access (SSH or Telnet) to the server or hosting account where X-Cart is installed.

### Restoring the database through X-Cart Admin area

To restore the database through the X-Cart Admin area:

1. Log in to the Admin area.

2. Go to the **Restore Database** tab in the **System Tools** -> **Database** section;
  ![restore.png]({{site.baseurl}}/attachments/ref_080K3Qe7/restore.png)

3. Restore the database from the SQL dump using the instructions below.
  
  (PREFERRED WAY) If the SQL dump is saved in the predefined file located on the server file system (file xcartdump.sql in directory <xcart_dir>/var/tmp/):
a) Click the Restore button.
b) Confirm the action.
c) Wait until the system displays a message saying that the database has been restored successfully.
If the SQL dump is saved on a local computer:
a) Click the Browse... button to display the dialog box for uploading files.
b) Select the file with the SQL dump.
c) Click the Restore from file button.
Wait until the system displays a message saying that the database has been restored successfully.
Maintaining-03.gif
Note: If your SQL dump is saved on your local computer, you can restore the database through the Admin area only if the size of the SQL dump does not exceed the value in line "WARNING! The maximum file size that can be uploaded:...". This value is defined by the PHP settings of your server. If you have access to the PHP configuration file php.ini, you can increase/decrease the maximum file size by editing the value of the variable $max_upload_size.
If changing the php.ini settings is not possible, you should rename your SQL dump to xcartdump.sql file, upload it to the directory <xcart_dir>/var/tmp/ (for example using FTP), then use the Restore button to restore the database from that file.
Restoring the database using terminal access
To restore the database using terminal access to the server:

1. Log in to your server or your hosting account.

2. Run the following shell command.

> mysql -h<sql_host> -u<sql_user> -p <sql_db> < <store_backup.sql>
If you connect to the database server through a non-typical port or socket, the command should be
mysql -P<sql_port> -h<sql_host> -u<sql_user> -p <sql_db> < <store_backup.sql>
or
mysql -S<sql_socket> -h<sql_host> -u<sql_user> -p <sql_db> < <store_backup.sql>
The system will ask you to to enter your password for the MySQL account. After the password has been accepted, the system will populate the database with the data from the SQL dump.

Important: The name/address of the MySQL server, the name of the MySQL database, the username and the password for the MySQL account must be the same as the values of the respective variables in the X-Cart configuration file config.php.
Safety Tips
Remove the SQL dump and the archive from the WWW directory of your server or hosting accoun. It is strongly recommended that you do not leave the SQL dump of the store database and the packed archive with X-Cart files anywhere in the WWW directory of your server or hosting account where you keep your Internet projects and which is publicly accessible. Otherwise, your store data can be easily stolen as anybody will be able to access the database dump through the Web.

A good practice here is to keep the backup on a local computer or in a directory on a remote server that cannot be accessed through the Web. For example, if the root directory of your hosting account is /u/user/ and the web directory is /u/user/public_html/, you must move the SQL dump and the store archive from the directory /u/user/public_html/ to somewhere in the directory /u/user/.

If you backed up the database through the X-Cart Admin area, make sure you have not left the dump (file xcartdump.sql) in the directory <xcart_dir>/var/tmp/, which is the pre-defined directory for the SQL dump generated by X-Cart.

Troubleshooting
Problem	Possible cause	Solution
The system says you do not have enough privileges to write to the file	User who has run the PHP script is not allowed to write files to the directory.	Set writable permissions to the directory where you are trying to save the SQL dump to, and repeat the task.
The system says you do not have enough free disk space to complete the operation.	File system does not have enough free disk space.	Since some data has been saved to the file before the error message, first remove the file with the backup. Then either make available more free space and repeat the task, or choose to save the file to another location.
Task was terminated and the system says you will be redirected to the previous page.	The memory that was allocated to the script has exhausted	Increase the amount of memory allocated to the script by increasing the default value of the $memory_limit variable in the php.ini file. If you do not have access to the php.ini file, ask your hosting team to help you.
Important: It may be necessary to increase the allocated memory several times, because it is impossible to predict how much memory you really need.
