---
title: "Task - Linux Process Troubleshooting"
seoTitle: "Linux Process Troubleshooting"
seoDescription: "Linux Process Troubleshooting"
datePublished: Wed Jun 14 2023 15:00:56 GMT+0000 (Coordinated Universal Time)
cuid: cljbk53gf000m09l276fga04m
slug: task-linux-process-troubleshooting
tags: linux, kodekloud, kodekloudengineer, kodekloudtasks, kodekloud-coupons

---

## **Problem:**

> ***The production support team of xFusionCorp Industries has deployed some of the latest monitoring tools to keep an eye on every service, application, etc. running on the systems. One of the monitoring systems reported about Apache service unavailability on one of the app servers in***`Stratos DC`.
> 
> ***Identify the faulty app host and fix the issue. Make sure Apache service is up and running on all app hosts. They might not hosted any code yet on these servers so you need not to worry about if Apache isn't serving any pages or not, just make sure service is up and running. Also, make sure Apache is running on port***`8087` on all app servers.

## Solution:

1. First of all, we need to ssh into all the 3 `app servers` and find out on which server the `Apache` service not working. So `SSH` into all servers and use this command to check **the** stat**u**s of the Apache service.
    
    ```plaintext
     sudo systemctl status httpd
    ```
    
2. Now, we know which server has the `Apache` service issue. So let's find out which process is consuming this port 8087 mentioned in the problem statement. In your case, it could be different
    
    ```plaintext
     sudo netstat -tunelp
    ```
    
3. So, from this command, you will know which process uses this port 8087. So kill this process & restart the Apache service, additionally, check the status too.
    
    ```plaintext
     sudo kill -9 419
     sudo systemctl restart httpd
     sudo systemctl status httpd
    ```
    

References: [**https://kodekloud.com/community/t/linux-process-troubleshooting-start-service-issue/6154/7**](https://kodekloud.com/community/t/linux-process-troubleshooting-start-service-issue/6154/7)