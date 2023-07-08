---
title: "Task- Linux User Expiry"
seoTitle: "Task- Linux User Expiry"
seoDescription: "Task- Linux User Expiry"
datePublished: Sat Jul 08 2023 16:35:18 GMT+0000 (Coordinated Universal Time)
cuid: clju88a2700040amoakm77c0n
slug: task-linux-user-expiry-1
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1688834104959/517fe5b0-2613-4f89-b54b-fed1c9531a50.png
tags: linux, kodekloud

---

## Problem:

> A developer kirsty has been assigned `Nautilus` project temporarily as a backup resource. As a temporary resource for this project, we need a temporary user for kirsty. It’s a good idea to create a user with a set expiration date so that the user won't be able to access servers beyond that point.
> 
>   
> 
> Therefore, create a user named `kirsty` on the `App Server 2`. Set `expiry date` to `2021-01-28` in `Stratos Datacenter`. Make sure the user is created as per standard and is in lowercase.

## Solution:

1. ssh into the app-server2
    
2. To create `kirsty` user with an expiry date, execute the following command.
    
    ```plaintext
    sudo useradd -e 2021-01-28 kirsty
    ```
    

Validate:

You can validate the created use with `id kirsty` command