---
title: "Task- Linux Configure sudo"
seoDescription: "Task35 - Linux Configure sudo, kodekloud"
datePublished: Wed May 10 2023 08:03:03 GMT+0000 (Coordinated Universal Time)
cuid: clhhey9h8000909lac4hre0u1
slug: task-linux-configure-sudo
tags: linux, linux-for-beginners, linux-basics, kodekloud, linuxadministrator

---

Problem:

> We have some users on all app servers in `Stratos Datacenter`. Some of them have been assigned some new roles and responsibilities, therefore their users need to be upgraded with sudo access so that they can perform admin level tasks.
> 
> a. Provide sudo access to user `kirsty` on all app servers.
> 
> b. Make sure you have set up password-less sudo for the user.
> 
> ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1683702822135/1e69328a-25a4-41a3-9a92-0b8be4169eb8.png align="center")

Solution:

1. ssh into all the app servers
    
2. Check if the user is existing or not
    
    ```plaintext
    id jim
    ```
    
3. Switch to root user `sudo su`
    
4. Edit the sudoers file using `visudo` the command. If you are not logged in as a root user then you have to use `sudo visudo`
    
5. At the end of the file enter this command
    
    ```plaintext
    kirsty ALL=(ALL) NOPASSWD: ALL
    ```
    
    Note: Remember `kirsty` is the user that we want to modify
    
6. To check whether this user has the proper permission or not hit the command
    
    ```plaintext
    sudo cat /etc/sudoers | grep kirsty
    ```
    

Note: We can use `cat /etc/passwd | grep kirsty` file to verify whether a user is exist or not from step 2

Article reference: [https://www.ibm.com/docs/en/zscc/1.1.0?topic=eylzsdg-enable-passwordless-sudo-access-your-linux-user-id](https://www.ibm.com/docs/en/zscc/1.1.0?topic=eylzsdg-enable-passwordless-sudo-access-your-linux-user-id)

\[https://www.simplified.guide/linux/enable-passwordless-sudo#:~:text=Steps%20configure%20passwordless%20sudo%20in%20Linux%3A&text=Check%20your%20current%20sudo%20privileges%20for%20your%20user%20account.&text=Use%20the%20visudo%20command%20to%20open%20the%20sudoers%20configuration%20file.&text=Add%20the%20line%20ALL%20%3D%20(ALL,commands%20without%20entering%20a%20password.\](https://www.simplified.guide/linux/enable-passwordless-sudo#:~:text=Steps%20configure%20passwordless%20sudo%20in%20Linux%3A&text=Check%20your%20current%20sudo%20privileges%20for%20your%20user%20account.&text=Use%20the%20visudo%20command%20to%20open%20the%20sudoers%20configuration%20file.&text=Add%20the%20line%20ALL%20%3D%20(ALL,commands%20without%20entering%20a%20password.)