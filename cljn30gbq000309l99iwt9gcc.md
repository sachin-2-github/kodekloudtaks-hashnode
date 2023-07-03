---
title: "Task - Disable Root Login"
seoTitle: "Task - Disable Root Login"
seoDescription: "Task - Disable Root Login"
datePublished: Mon Jul 03 2023 16:34:52 GMT+0000 (Coordinated Universal Time)
cuid: cljn30gbq000309l99iwt9gcc
slug: task-disable-root-login
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1688402839634/91d5aa6b-4869-4789-aed4-4e29b7c4fc2d.png
tags: kodekloud

---

## Problem:

> After doing some security audits of servers, `xFusionCorp Industries` security team has implemented some new security policies. One of them is to disable direct root login through SSH.
> 
>   
> 
> Disable direct SSH root login on all app servers in `Stratos Datacenter`.

## Solution:

1. ssh into all app servers and repeat the below steps.
    
2. Edit the `/etc/ssh/sshd_config` file and change `PermitRootLogin yes` it to `PermitRootLogin no` save the file. Don't forget to uncomment this line before saving the file.
    
3. ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688401929543/a94f4d94-f5f4-4966-865e-899f104adaca.png align="center")
    
    Restart the `sshd` service.
    

## Reference:

[https://www.vultr.com/docs/disable-or-restrict-root-login-via-ssh-on-linux/?utm\_source=performance-max-apac&utm\_medium=paidmedia&obility\_id=16876059738&utm\_adgroup=&utm\_campaign=&utm\_term=&utm\_content=&gclid=CjwKCAjw44mlBhAQEiwAqP3eVtDuOvin5QH1rLMjg1K3HgIqQTd4k16RzQZCggCuun-ytn0y2E-kEBoCpFoQAvD\_BwE](https://www.vultr.com/docs/disable-or-restrict-root-login-via-ssh-on-linux/?utm_source=performance-max-apac&utm_medium=paidmedia&obility_id=16876059738&utm_adgroup=&utm_campaign=&utm_term=&utm_content=&gclid=CjwKCAjw44mlBhAQEiwAqP3eVtDuOvin5QH1rLMjg1K3HgIqQTd4k16RzQZCggCuun-ytn0y2E-kEBoCpFoQAvD_BwE)