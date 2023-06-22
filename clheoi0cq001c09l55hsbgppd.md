---
title: "Task 33-Web Server Security"
seoTitle: "kodekloud Task 32-Web Server Security"
datePublished: Mon May 08 2023 10:07:03 GMT+0000 (Coordinated Universal Time)
cuid: clheoi0cq001c09l55hsbgppd
slug: task-33-web-server-security
tags: linux, linux-for-beginners, linuxadministrator

---

Problem:

> During a recent security audit, the application security team of XFusionCorp Industries found security issues with the
> 
> Apache web server on Nautilus App Server 3 server in Stratos DC. They have listed several security issues that need to be fixed on this server. Please apply the security settings below:
> 
> 1. On Nautilus App Server 3 it was identified that the Apache web server is exposing the version number. Ensure this server has the appropriate settings to hide the version number of the Apache web server.
>     
> 2. There is a website hosted under /var/www/html/official on
>     
> 
> App Server 3. It was detected that the directory /official lIsts all of its contents while browsing the URL. Disable the directory browser listing in Apache config.
> 
> c. Also make sure to restart the Apache service after making the changes
> 
> ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1683524565574/1ff77e24-9ea9-468e-8015-62f7b9c83696.png align="left")

Solution:

1. ssh into App server 3
    
2. Navigate to /etc/httpd/conf/httpd.conf file and edit this file
    
3. To hide the Version number of the apache web server make the changes `ServerSignature on` and `ServerTokens Full` as follows.
    
    ```plaintext
    ServerSignature On
    ServerTokens Full
    ```
    
    Note: If you don't find these lines under the conf file then add these lines to the end of the file and save it.
    
4. To Disable the directory browser listing. Edit the same file and replace this line `Options Indexes FollowSymLinks`under &lt;Directory&gt; tab. It'll look similar to this
    
    ```plaintext
    <Directory /var/www/html>
        Options Indexes FollowSymLinks
        AllowOverride All
        Require all granted
    </Directory>
    ```
    
5. Remove the `Indexes` option from the `Options` directive, so that it looks like this:
    
    This will disable the directory listing for the directory.
    
    ```plaintext
    Options FollowSymLinks
    ```
    
6. Restart the httpd service
    
    ```plaintext
    sudo systemctl restart httpd
    ```
    

Note: I have performed all the changes on Centos which is a RHEL-based OS but if you have any Debian-based system like Ubuntu then the steps would be a bit different.

Article reference:

[https://tecadmin.net/hide-apache-version-from-http-header/#:~:text=The%20simplest%20way%20to%20hide,the%20%E2%80%9CServer%E2%80%9D%20header%20field](https://tecadmin.net/hide-apache-version-from-http-header/#:~:text=The%20simplest%20way%20to%20hide,the%20%E2%80%9CServer%E2%80%9D%20header%20field).

[https://stackoverflow.com/questions/2530372/how-do-i-disable-directory-browsing](https://stackoverflow.com/questions/2530372/how-do-i-disable-directory-browsing)