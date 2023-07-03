---
title: "Task- Linux Banner"
seoTitle: "Task- Linux Banner"
seoDescription: "Task- Linux Banner"
datePublished: Sun Jul 02 2023 15:47:12 GMT+0000 (Coordinated Universal Time)
cuid: cljllvayw000m0amfhn1c88qa
slug: task-linux-banner
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1688402388465/638d5e87-469a-4309-af76-135671596849.png
tags: linux, kodekloud

---

## Problem:

> During the monthly compliance meeting, it was pointed out that several servers in the `Stratos DC` do not have a valid banner. The security team has provided serveral approved templates which should be applied to the servers to maintain compliance. These will be displayed to the user upon a successful login.
> 
> Update the `message of the day` on all application and db servers for `Nautilus`. Make use of the approved template located at `/home/thor/nautilus_banner` on jump host

## Solution:

1. ssh into all app-servers and db-serer.
    
2. Switch to root user using `sudo su`
    
3. Copy the banner template from `jump-server` to the `app-server`
    
    ```plaintext
    scp thor@jump_host.stratos.xfusioncorp.com:/home/thor/nautilus_banner /home/tony/
    ```
    
4. Now copy this template to the '`message of the day`" file".
    
    ```plaintext
    cp /home/tony/nautilus_banner /etc/motd
    ```
    
    If prompted to override, enter 'Yes' to proceed.
    
5. Repeat all the steps on all `app-servers` and `db-server.`
    

## Error:

You might face a problem with `SCP` when you `ssh` into `db-server`, If yes, just install `open-ssh` on it and then do all the steps you did for `app-server's.`

```plaintext
sudo yum install open-ssh -y
```

For further details on the error and its resolution, please refer to the Kodekloud community channel [**here**](https://kodekloud.com/community/t/linux-banner-task-issue/9150/6).

## Reference:

[https://www.cyberciti.biz/faq/how-can-i-change-the-message-of-the-day-on-my-linux-server/#:~:text=The%20abbreviation%20%E2%80%9Cmotd%E2%80%9D%20stands%20for,edit%20%2Fetc%2Fmotd%20file](https://www.cyberciti.biz/faq/how-can-i-change-the-message-of-the-day-on-my-linux-server/#:~:text=The%20abbreviation%20%E2%80%9Cmotd%E2%80%9D%20stands%20for,edit%20%2Fetc%2Fmotd%20file)