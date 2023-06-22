---
title: "Task 36- Linux Find Command"
seoTitle: "ask 36- Linux Find Command"
seoDescription: "ask 36- Linux Find Command"
datePublished: Thu May 11 2023 09:58:38 GMT+0000 (Coordinated Universal Time)
cuid: clhiyiqy9000309mggacvfrk8
slug: task-36-linux-find-command
tags: linux, linux-for-beginners, linux-commands, kodekloud

---

### Problem:

> During a routine security audit, the team identified an issue on the Nautilus App Server. Some malicious content was identified within the website code. After digging into the issue they found that there might be more infected files. Before doing a cleanup they would like to find all similar files and copy them to a safe location for further investigation. Accomplish the task as per the following requirements:
> 
>   
> 
> a. On `App Server 1` at location `/var/www/html/ecommerce` find out all files (not directories) having `.js` extension.
> 
> b. Copy all those files along with their `parent directory structure` to location `/ecommerce` on same server.
> 
> c. Please make sure not to copy the entire `/var/www/html/ecommerce` directory content.  
>   
> 
> ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1683797272456/38cfb21b-afad-42e5-8349-362fbde14001.png align="center")

### Solution:

1. ssh into app server1
    
2. Swtich to root access `sudo su`
    
3. Supply this command
    
    ```plaintext
    find /var/www/html/ecommerce -type f -name "*.js" -exec cp --parents {} /ecommerce \;
    ```
    
    The "-type f" option specifies that it should only look for files, not directories. The "-name" option specifies the file name pattern to search for. The "-exec" option is used to execute the "cp" command with the "--parents" option, which creates the directory structure while copying the files, and the "{}" is a placeholder for the found file names. The backslash ";" at the end of the command indicates the end of the command.