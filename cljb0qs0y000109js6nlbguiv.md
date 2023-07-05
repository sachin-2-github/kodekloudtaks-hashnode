---
title: "Task  -  Add Response Headers in Apache"
seoTitle: "Add Response Headers in Apache"
seoDescription: "Add Response Headers in Apache"
datePublished: Sun Jun 25 2023 05:58:07 GMT+0000 (Coordinated Universal Time)
cuid: cljb0qs0y000109js6nlbguiv
slug: task-add-response-headers-in-apache
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1688543053330/94ed66c8-9e56-4258-8572-7c0fb24995b9.jpeg
tags: linux, linux-for-beginners, kodekloud

---

## Problem:

> We are working on hardening Apache web server on all app servers. As a part of this process we want to add some of the Apache response headers for security purpose. We are testing the settings one by one on all app servers. As per details mentioned below enable these headers for Apache:
> 
> 1. Install `httpd` package on `App Server 2` using yum and configure it to run on `6000` port, make sure to start its service.
>     
> 2. Create an `index.html` file under Apache's default document root i.e `/var/www/html` and add below given content in it.
>     
>     `Welcome to the xFusionCorp Industries!`
>     
> 3. Configure Apache to enable below mentioned headers:
>     
>     `X-XSS-Protection` header with value `1; mode=block`
>     
>     `X-Frame-Options` header with value `SAMEORIGIN`
>     
>     `X-Content-Type-Options` header with value `nosniff`
>     
> 
> `Note:` You can test using curl on the given app server as LBR URL will not work for this task.

## Solution:

  
*<mark>Please ensure to review the task instructions carefully and modify the commands according to your specific server, username, and other relevant details.</mark>*

1. ssh into app-server2
    
2. Install the `httpd` package using yum
    
    ```plaintext
    sudo yum install httpd -y
    ```
    
3. Configure `httpd` to run on port `6000`
    
    ```plaintext
    sudo sed -i 's/Listen 80/Listen 6000/g' /etc/httpd/conf/httpd.conf
    ```
    
4. Start the `httpd` service
    
    ```plaintext
    sudo systemctl start httpd
    ```
    
5. Create index.html and insert `Welcome to the xFusionCorp Industries!` into it and save it
    
    ```plaintext
    sudo touch /var/www/htmlindex.html
    sudo vi /var/www/htmlindex.html
    ```
    
6. Open the Apache configuration file using a text editor and Add the following lines within the file, locate the `<Directory "/var/www/html">` section to enable the desired headers in the file.
    
    ```plaintext
    Header always set X-XSS-Protection "1; mode=block"
    Header always set X-Frame-Options "SAMEORIGIN"
    Header always set X-Content-Type-Options "nosniff"
    ```
    
7. Save the changes and exit the text editor.
    
8. Restart the Apache service to apply the configuration changes:
    
    ```plaintext
    sudo systemctl restart httpd
    ```
    

After following these steps, Apache will be configured to enable the `X-XSS-Protection, X-Frame-Options, and X-Content-Type-Options` headers with the specified values. You can test the configuration using curl or any other HTTP client tool on the app server.

## Validation:

```plaintext
curl -I http://localhost:6000
```