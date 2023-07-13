---
title: "Task- Linux User Expiry"
seoTitle: "Task- Linux User Expiry"
seoDescription: "Task- Linux User Expiry"
datePublished: Sat Jul 08 2023 10:30:57 GMT+0000 (Coordinated Universal Time)
cuid: cljtv7pdp000n0al3gf9debl8
slug: task-linux-user-expiry
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1689226335990/a86fca62-90f9-4c55-ad53-00896264d66d.avif
tags: linux, kodekloud

---

## Problem:

> A developer kirsty has been assigned `Nautilus` project temporarily as a backup resource. As a temporary resource for this project, we need a temporary user for kirsty. It’s a good idea to create a user with a set expiration date so that the user won't be able to access servers beyond that point.
> 
> Therefore, create a user named `kirsty` on the `App Server 2`. Set `expiry date` to `2021-01-28` in `Stratos Datacenter`. Make sure the user is created as per standard and is in lowercase.

## Solution:

1. ssh into the app-server2
    
2. To create `kirsty` user with an expiry date, execute the following command.
    
    ```plaintext
    sudo useradd -e 2021-01-28 kirsty
    ```