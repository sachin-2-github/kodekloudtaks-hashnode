---
title: "Task - Apache Redirects"
seoTitle: "Apache Redirects"
seoDescription: "kodekloud"
datePublished: Thu Jun 08 2023 17:05:19 GMT+0000 (Coordinated Universal Time)
cuid: cline3bqo000909m79njzfxcq
slug: task-apache-redirects
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1689226445417/b6cb1a68-efd2-46d1-ae3e-eb8b515f8af8.jpeg
tags: linux, devops, linux-for-beginners

---

## Problem:

> The Nautilus devops team got some requirements related to some Apache config changes. They need to setup some redirects for some URLs. There might be some more changes need to be done. Below you can find more details regarding that:
> 
> 1. `httpd` is already installed on `app server 1`. Configure Apache to listen on port `8085`.
>     
> 2. Configure Apache to add some redirects as mentioned below:
>     
>     a.) Redirect [`http://stapp01.stratos.xfusioncorp.com:<Port>/`](http://stapp01.stratos.xfusioncorp.com:%3CPort%3E/) to [`http://www.stapp01.stratos.xfusioncorp.com:<Port>/`](http://www.stapp01.stratos.xfusioncorp.com:%3CPort%3E/) i.e `non www` to `www`. This must be a permanent redirect i.e `301`
>     
>     b.) Redirect [`http://www.stapp01.stratos.xfusioncorp.com:<Port>/blog/`](http://www.stapp01.stratos.xfusioncorp.com:%3CPort%3E/blog/) to [`http://www.stapp01.stratos.xfusioncorp.com:<Port>/news/`](http://www.stapp01.stratos.xfusioncorp.com:%3CPort%3E/news/). This must be a temporary redirect i.e `302`.
>     

## Solution:

1. ssh into app server 1 with sudo privileges
    
2. Edit the httpd conf file
    
    `/sudo vi /etc/httpd/conf/httpd.conf`
    
3. Locate the line that specifies the "Listen" directive and change the port to 8085:
    
    `Listen 8085`
    
4. Configure the permanent redirect (301) from non-www to www:
    

```plaintext
<VirtualHost *:8085>
    ServerName stapp01.stratos.xfusioncorp.com:8085/
    Redirect 301 / http://www.stapp01.stratos.xfusioncorp.com:8085/
</VirtualHost>
```

1. Configure the temporary redirect (302) from /blog/ to /news/:
    

```plaintext
<VirtualHost *:8085>
    ServerName www.stapp01.stratos.xfusioncorp.com:8085/blog/
    Redirect 302 /blog/ http://www.stapp01.stratos.xfusioncorp.com:8085/news/
</VirtualHost>
```

1. Save the changes and exit the editor.
    
2. Restart the Apache service for the changes to take effect:
    

```plaintext
systemctl restart httpd
```

With these updated configurations, the non-www URLs will be permanently redirected to the www URLs with a 301 status code, and the /blog/ URL will be temporarily redirected to the /news/ URL with a 302 status code.

Note: You can check the redirected URLs and their status using the curl command

```plaintext
curl http://stapp01.stratos.xfusioncorp.com:8085/
curl http://www.stapp01.stratos.xfusioncorp.com:8085/blog/
```

References: [https://ubiq.co/tech-blog/redirect-site-another-domain/](https://ubiq.co/tech-blog/redirect-site-another-domain/)