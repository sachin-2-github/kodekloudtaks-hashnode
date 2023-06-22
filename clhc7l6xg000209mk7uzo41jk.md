---
title: "Task 32- Linux LogRotate"
datePublished: Sat May 06 2023 16:38:05 GMT+0000 (Coordinated Universal Time)
cuid: clhc7l6xg000209mk7uzo41jk
slug: task-32-linux-logrotate
tags: linux, linux-for-beginners, linux-commands

---

Problem: Linux LogRotate

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1683374548341/0c441703-f3b0-4571-a068-e8d03be8417d.png align="center")

Solution:

1. ssh into all app servers.
    
2. install httpd using this command
    
    ```plaintext
    sudo yum install httpd -y
    ```
    
3. Navigate to /etc/logrotate.d/httpd and edit the httpd config file and add these lines.
    
    ```plaintext
    monthly 
    rotate 3
    ```
    
    Screenshot
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1683390777454/d5965d91-dc27-496f-9aa0-725ed73c2963.png align="center")
    
4. Save the file. Done
    

Article Reference: [https://www.thegeekstuff.com/2010/07/logrotate-examples/](https://www.thegeekstuff.com/2010/07/logrotate-examples/)