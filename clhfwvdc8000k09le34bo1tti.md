---
title: "Task- Application Security"
seoTitle: "kodekloud task 32- application security, iptables, firewall"
seoDescription: "This article helps to solve the #kodekloud task 32nd challenge under sys admin category"
datePublished: Tue May 09 2023 06:49:09 GMT+0000 (Coordinated Universal Time)
cuid: clhfwvdc8000k09le34bo1tti
slug: task-application-security
tags: linux, security, firewall, linux-for-beginners, kodekloud

---

Problem:

> We have a backup management application UI hosted on
> 
> Nautilus's backup server in Stratos DC. That backup management application code is deployed under Apache on the backup server itself, and Nginx is running as a reverse proxy on the same server. Apache and Nainx ports are 6200 and 8097 respectively. We have iptables firewall installed on this server.
> 
> Make the appropriate changes to fulfill the requirements mentioned below:
> 
> We want to open all incoming connections to Nginx's port and block all incoming connections to Apache's port. Also
> 
> ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1683613088238/f0f0f30e-cf78-46fa-b2b6-362642f0309c.png align="left")

Solution:

1. ssh into the backup server
    
2. Open the `iptables` firewall configuration file using the following command
    
    ```plaintext
    sudo nano /etc/sysconfig/iptables
    ```
    
3. Add the following lines to open all incoming connections to Nginx's port and block all incoming connections to Apache's port:
    
    ```plaintext
    -A INPUT -p tcp --dport 8097 -j ACCEPT
    -A INPUT -p tcp --dport 6200 -j DROP
    ```
    
    1. Save the file
        
    2. Restart the `iptables` service
        
        ```plaintext
        sudo systemctl restart iptables
        ```
        

Reference:  
`iptables is a powerful Linux-based firewall utility that allows network administrators to configure and manage netfilter rules to filter network traffic. It is a tool for managing firewall rules and routing tables on Linux systems. iptables is typically used to secure a server or network by preventing unauthorized access and filtering unwanted traffic. It can be used to block specific IP addresses or ports, filter packets based on protocols or connection states, and more. iptables is a fundamental component of Linux network security and is included in most Linux distributions.`