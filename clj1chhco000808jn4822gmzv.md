---
title: "Task - Install And Configure SFTP"
seoTitle: "Install And Configure SFTP"
seoDescription: "Install And Configure SFTP"
datePublished: Sun Jun 18 2023 11:29:07 GMT+0000 (Coordinated Universal Time)
cuid: clj1chhco000808jn4822gmzv
slug: task-install-and-configure-sftp
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1688402655416/5ec13d6c-389f-4df3-8e1a-1dcce4947e38.webp
tags: linux, kodekloud

---

## Problem:

> Some of the developers from `Nautilus` project team have asked for SFTP access to at least one of the app server in `Stratos DC`. After going through the requirements, the system admins team has decided to configure the SFTP server on `App Server 1` server in `Stratos Datacenter`. Please configure it as per the following instructions:
> 
> a. Create an SFTP user `rose` and set its password to `TmPcZjtRQx`.
> 
> b. Password authentication should be enabled for this user.
> 
> c. Set its ChrootDirectory to `/var/www/data`.
> 
> d. SFTP user should only be allowed to make SFTP connections.

## Solution:

*<mark>Please ensure to review the task instructions carefully and modify the commands according to your specific server, username, and other relevant details.</mark>*

1. ssh into app server1
    
2. Create an SFTP user named " rose" with the password "TmPcZjtRQx". Run the following command:
    
    ```plaintext
    sudo useradd -m -s /sbin/nologin rose
    sudo passwd rose
    ```
    
    You will be prompted to enter and confirm the password for the user "rose". Copy and paste "TmPcZjtRQx" as the password when prompted on the terminal.
    
3. Open the SSH server configuration file using a text editor.
    
    ```plaintext
    sudo vi /etc/ssh/sshd_config
    ```
    
4. Locate the section in the `sshd_config` file that starts with `Subsystem sftp` and modify it as follows:
    
    ```plaintext
    #Subsystem sftp /usr/libexec/openssh/sftp-server
    Subsystem sftp internal-sftp
    ```
    
    Comment out the original `Subsystem sftp` line and replace it with `Subsystem sftp internal-sftp`. This configuration ensures that the SFTP subsystem is used for SFTP connections.
    
5. Add the following lines at the end of the file, This will enable `PasswordAuthentication` as well as set `ChrootDirectory`
    
    ```plaintext
    Match User rose
        ForceCommand internal-sftp
        PasswordAuthentication yes
        ChrootDirectory /var/www/data
        PermitTunnel no
        AllowAgentForwarding no
        AllowTcpForwarding no
        X11Forwarding no
    ```
    

*Note: Maintain the indentation here.*

1. Now create this directory.
    
    ```plaintext
    sudo mkdir -p /var/www/data
    ```
    
2. Set the correct ownership and permissions for the directory using the following commands:
    
    ```plaintext
    sudo chown root:root /var/www/data
    sudo chmod 755 /var/www/data
    ```
    
3. Finally, Restart the ssh service
    
    ```plaintext
    sudo systemctl restart sshd
    ```
    
4. If you want to check the `sftp` connection then follow the command
    
    ```plaintext
    sftp rose@<app-server1-IP/hostname>
    ```
    
    <mark>Remember to replace app-server1 with your app server's IP or hostname. This command will ask for the password enter the password for this provided in the task.</mark>