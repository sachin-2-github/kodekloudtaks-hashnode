---
title: "Task 43 - IPtables Installation And Configuration"
seoTitle: "IPtables Installation And Configuration"
seoDescription: "IPtables Installation And Configuration"
datePublished: Sun Jun 18 2023 12:15:42 GMT+0000 (Coordinated Universal Time)
cuid: clj1e5e4o000109jj2a9x8irx
slug: task-43-iptables-installation-and-configuration
tags: kodekloud

---

## Problem:

> We have one of our websites up and running on our `Nautilus` infrastructure in `Stratos DC`. Our security team has raised a concern that right now Apache’s port i.e `5001` is open for all since there is no firewall installed on these hosts. So we have decided to add some security layer for these hosts and after discussions and recommendations we have come up with the following requirements:
> 
>   
> 
> 1. Install `iptables` and all its dependencies on each app host.
>     
> 2. Block incoming port `5001` on all apps for everyone except for LBR host.
>     
> 3. Make sure the rules remain, even after system reboot.
>     

## Solution:

*<mark>Please ensure to review the task instructions carefully and modify the commands according to your specific server, username, and other relevant details.</mark>*

1. ssh into all app servers and perform these steps on all app servers.
    
2. Install `iptables`
    
    ```plaintext
    sudo yum install iptables -y
    ```
    
3. Create a new `iptables` rule to block incoming connections on port 5001, except for the [LBR host](https://kodekloudhub.github.io/kodekloud-engineer/docs/projects/nautilus#infrastructure-details:~:text=stlb01,Nautilus%20HTTP%20LBR). Run the following command:
    
    ```plaintext
    sudo iptables -A INPUT -p tcp --dport 5001 -s 172.16.238.14 -j ACCEPT
    sudo iptables -A INPUT -p tcp --dport 5001 -j DROP
    ```
    

*Remember 172.16.238.14 is our LBR host IP*

1. Save the `iptables` rules to persist after the system reboot.
    
    ```plaintext
    sudo iptables-save | sudo tee /etc/sysconfig/iptables
    ```
    

## Verify:

To verify whether the rules are properly working or not try `curl` to apache server.

1. ssh into the LBR server.
    
2. Try curl command
    

```plaintext
curl -I http://<any-app-sever:5001>
```

*Remember in place of* `any-app-seve`*r put the* `IP` *or* `hostname` *of any app servers. Check one by one for all 3 app servers. It should give* `200 ok` *response*

## Error:

No errors were encountered while performing this task.