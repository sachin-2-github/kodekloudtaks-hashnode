---
title: "Setup SSL for Nginx"
seoTitle: "Setup SSL for Nginx"
seoDescription: "Setup SSL for Nginx"
datePublished: Thu Jun 29 2023 17:24:54 GMT+0000 (Coordinated Universal Time)
cuid: cljhf1ee300000amkb3shftzw
slug: setup-ssl-for-nginx
tags: linux, kodekloud

---

## Problem:

> The system admins team of `xFusionCorp Industries` needs to deploy a new application on `App Server 3` in `Stratos Datacenter`. They have some pre-requites to get ready that server for application deployment. Prepare the server as per requirements shared below:
> 
> 1. Install and configure `nginx` on `App Server 3`.
>     
> 2. On `App Server 3` there is a self signed SSL certificate and key present at location `/tmp/nautilus.crt` and `/tmp/nautilus.key`. Move them to some appropriate location and deploy the same in Nginx.
>     
> 3. Create an `index.html` file with content `Welcome!` under Nginx document root.
>     
> 4. For final testing try to access the `App Server 3` link (either hostname or IP) from `jump host` using curl command. For example `curl -Ik https://<app-server-ip>/`.
>     

## Solution:

1. ssh into the App server3 with the sudo privileges
    
2. Install the EPEL repo for the Nginx package
    

```plaintext
 sudo yum install epel-release -y
```

1. Install Nginx
    

```plaintext
sudo yum install nginx -y
```

1. Check version
    

```plaintext
nginx -v
```

1. Start the Nginx service and check the status.
    

```plaintext
sudo systemctl start nginx && systemctl status nginx
```

1. Enable this service
    

```plaintext
sudo systemctl enable nginx
```

*Now we have installed the Nginx properly*

Let's do some configurations

* Create `index.html` file under the nginx root directory
    
* To see the Root directory of the nginx Navigate to `/usr/share/nginx/html` directory
    
* Now do `ls -al /usr/share/nginx/html/index.html`
    

*Note: You will find a link* `index.html` *pointing to the original file. Go to that pointed file and edit that* `index.html` *file. If it exists there o/w create a new file under that directory. So in our case, the HTML directory was created under the '*`doc/`*' directory. So I had to create it and edit the index.html file*

The steps I did were

* Created HTML directory
    
* Created index.html file under it ( i.e HTML/index.html)
    
* Added HTML content `Welcome!` inside index.html
    

1. Copy or move the `nautilus.crt` and `nautilus.key` under `/etc/nginx/` directory
    
2. Edit the config file located at `/etc/ngix/nginx.conf` . Uncomment the entire server block and mention the certificate and key file path like below.
    

```plaintext
ssl_certificate     /etc/nginx/nautilus.crt;
ssl_certificate_key  /etc/nginx/nautilus.key;
```

1. Restart the Nginx server
    

```plaintext
systemctl restart nginx
```

1. Access the site with the curl command
    

```plaintext
curl -Ik https://<Ip/hostname of app-server3>
```

1. Response should be `200 ok.`