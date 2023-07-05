---
title: "Task - Create a Linux User with non-interactive shell"
seoTitle: "Task - Create a Linux User with non-interactive shell"
seoDescription: "Task - Create a Linux User with non-interactive shell"
datePublished: Wed Jul 05 2023 07:30:44 GMT+0000 (Coordinated Universal Time)
cuid: cljpegea0002s0al612400moo
slug: task-create-a-linux-user-with-non-interactive-shell
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1688542209009/4d1879bc-d517-4986-abc7-1e73c21b7efa.jpeg
tags: kodekloud

---

## Problem:

> The System admin team of `xFusionCorp Industries` has installed a backup agent tool on all app servers. As per the tool's requirements they need to create a user with a non-interactive shell.
> 
> Therefore, create a user named `yousuf` with a non-interactive shell on the `App Server 3`

## Solution:

*<mark>Please ensure to review the task instructions carefully and modify the commands according to your specific server, username, and other relevant details.</mark>*

1. ssh into `app-server3`
    
2. Add a user with a non-interactive shell
    
    ```plaintext
    sudo useradd -s /sbin/nologin yousuf
    ```
    
3. Check whether the user is created or not with the `id` command. If yes then you have successfully created a user.
    
    ```plaintext
    id yousuf
    ```