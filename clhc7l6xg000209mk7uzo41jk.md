---
title: "Task - Linux LogRotate"
datePublished: Sat May 06 2023 16:38:05 GMT+0000 (Coordinated Universal Time)
cuid: clhc7l6xg000209mk7uzo41jk
slug: task-linux-logrotate
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1688403272726/da767ee3-f4c6-4ad8-939b-85970e709d78.jpeg
tags: linux, linux-for-beginners, linux-commands

---

## Problem:

> The `Nautilus` DevOps team is ready to launch a new application, which they will deploy on app servers in `Stratos` `Datacenter`. They are expecting significant traffic/usage of httpd on app servers after that. This will generate massive logs, creating huge log files. To utilise the storage efficiently, they need to compress the log files and need to rotate old logs. Check the requirements shared below:  
>   
> a. In all app servers install `httpd` package.  
> b. Using `logrotate` configure `httpd` logs rotation to monthly and keep only 3 rotated logs (If by default log rotation is set, then please update configuration as needed)

## Solution:

1. ssh into all app servers.
    
2. Install `httpd` using this command
    
    ```plaintext
    sudo yum install httpd -y
    ```
    
3. Navigate to `/etc/logrotate.d/httpd` and edit the `httpd` config file and add these lines.
    
    ```plaintext
    monthly 
    rotate 3
    ```
    
    Screenshot
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1683390777454/d5965d91-dc27-496f-9aa0-725ed73c2963.png align="center")
    
4. Save the file. Done
    

## Reference:

[https://www.thegeekstuff.com/2010/07/logrotate-examples/](https://www.thegeekstuff.com/2010/07/logrotate-examples/)