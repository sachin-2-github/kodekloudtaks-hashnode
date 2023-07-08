---
title: "Task - Linux Postfix Mail Server"
seoTitle: "Linux Postfix Mail Server"
seoDescription: "Task 39- Linux Postfix Mail Server"
datePublished: Wed Jun 14 2023 15:06:31 GMT+0000 (Coordinated Universal Time)
cuid: cljbkc6lu001e09l8gox4d4wv
slug: task-linux-postfix-mail-server
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1688403002899/80da7382-4729-48dd-85ca-5b9867081ac8.png
tags: linux, kodekloud

---

## **Problem:**

> `xFusionCorp Industries` has planned to set up a common email server in `Stork DC`. After several meetings and recommendations they have decided to use `postfix` as their `mail transfer agent` and `dovecot` as an `IMAP/POP3` server. We would like you to perform the following steps:
> 
> 1. ***Install and configure*** `postfix` on `Stork DC` mail server.
>     
> 2. ***Create an email account*** [`rose@stratos.xfusioncorp.com`](mailto:rose@stratos.xfusioncorp.com) identified by `ksH85UJjhb`.
>     
> 3. ***Set its mail directory to*** `/home/rose/Maildir`.
>     
> 4. ***Install and configure*** `dovecot` on the same server.
>     

## Solution:

*<mark>Please ensure to review the task instructions carefully and modify the commands according to your specific server, username, and other relevant details.</mark>*

*Note: For me, the task is for* `rose` *So I have created this documentation keeping this user. But it might be different for you so keep in mind before performing commands from this article.*

1. ssh into the mail server with sudo privileges
    
2. install postfix
    
    ```plaintext
     sudo yum install postfix -y
    ```
    
3. install dovecot
    
    ```plaintext
     sudo yum install dovecot -y
    ```
    
4. Edit `/etc/postfix/main.cf` file and modify the fields from this file below and save it.
    
    `myhostname =` [`mail.stratos.xfusioncorp.com`](http://mail.stratos.xfusioncorp.com)
    
    `mydomain =` [`stratos.xfusioncorp.com`](http://stratos.xfusioncorp.com)
    
    `myorigin = $mydomain`
    
    `inet_interfaces = all`
    
    `#inet_interfaces =` [`localhost`](http://localhost)
    
    `mydestination = $myhostname` [`localhost`](http://localhost)`.$mydomain,` [`localhost`](http://localhost)`, $mydomain`
    
    `home_mailbox = Maildir/`
    
    *Note: In most cases this last field* `inet_interfaces =` [`localhost`](http://localhost) *is uncommented so comment it out*
    
5. Create the mail user account which is rose.
    
    ```plaintext
     sudo yum useradd -m rose
    ```
    
6. Set the password provided in the task. In our case it's '`ksH85UJjhb'`
    
    ```plaintext
     sudo yum passwd rose
    ```
    
7. Create the directory `/home/rose/Maildir` & Change the ownership and permissions as below
    
    ```plaintext
     sudo mkdir /home/rose/Maildir
     sudo chown -R rose:rose /home/rose/Maildir
     sudo chmod -R 700 /home/rose/Maildir
    ```
    
8. Configure created user in postfix Virtual Mailbox
    
    ```plaintext
     echo "rose@stratos.xfusioncorp.com rose/Maildir/" | sudo tee -a /etc/postfix/vmailbox
    ```
    
9. Edit the `/etc/dovecot/dovecot.conf` file and add the following lines anywhere in the file.
    
    `listen = *`
    
    `mail_location = maildir:/home/%u/Maildir`
    
    `auth_username_format = %u`
    
10. Edit `/etc/dovecot/conf.d/10-auth.conf` file and change `disable_plaintext_auth = yes` to `no` then uncomment and save it.
    
11. Edit `/etc/dovecot/conf.d/10-ssl.conf` file and change `ssl = required` and change it to `ssl = yes` and save the file
    
12. Generate SSL for `Dovecot`.
    
    ```plaintext
    sudo openssl req -new -x509 -days 365 -nodes -out /etc/pki/dovecot/certs/dovecot.pem -keyout /etc/pki/dovecot/private/dovecot.pem
    ```
    
    Remember: This command will give you a prompt, Just press `Enter` key for each option, Do not provide any text input.
    
13. Set ownership permissions.
    
    ```plaintext
    sudo chown -R dovecot:dovecot /etc/pki/dovecot
    sudo chmod 400 /etc/pki/dovecot/private/dovecot.pem
    ```
    
14. Finally, restart both services and enjoy the points.
    
    ```plaintext
    sudo systemctl restart postfix
    sudo systemctl restart dovecot
    ```
    

References: [**https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-postfix-as-a-send-only-smtp-server-on-ubuntu-22-04**](https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-postfix-as-a-send-only-smtp-server-on-ubuntu-22-04)

[**https://www.nbtechsupport.co.in/2021/06/linux-postfix-troubleshooting.html**](https://www.nbtechsupport.co.in/2021/06/linux-postfix-troubleshooting.html)