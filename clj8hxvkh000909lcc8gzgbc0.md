---
title: "Task 46 - Install a package"
seoTitle: "Install a package"
seoDescription: "Install a package"
datePublished: Fri Jun 23 2023 11:36:13 GMT+0000 (Coordinated Universal Time)
cuid: clj8hxvkh000909lcc8gzgbc0
slug: task-46-install-a-package
tags: linux, kodekloud

---

## Problem:

> As per new application requirements shared by the `Nautilus` project development team, serveral new packages need to be installed on all app servers in `Stratos Datacenter`. Most of them are completed except for `vsftpd`.
> 
> Therefore, install the `vsftpd` package on all `app-servers`.

## Solution:

1. ssh into all app servers and supply the following commands
    
2. Install
    
    ```plaintext
    sudo yum install vsftpd -y 
    ```
    
3. Check the version to verify the installation.
    
    ```plaintext
    vsftpd -v
    ```
    
4. Enable this service.
    
    ```plaintext
    sudo systemctl enable vdftpd
    ```
    
5. Start this service
    
    ```plaintext
    sudo systemctl start vsftpd
    ```
    
6. Check the status of the service. It should be in running status.
    
    ```plaintext
    sudo systemctl status vsftpd
    ```
    

## Validation:

vsftpd service should in running on all `app-servers.`