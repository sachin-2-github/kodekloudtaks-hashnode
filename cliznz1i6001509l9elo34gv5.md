---
title: "Task - Install and Configure Tomcat Server"
seoTitle: "Install and Configure Tomcat Server"
seoDescription: "Install and Configure Tomcat Server, 
The Nautilus application development team recently finished the beta version of one of their Java-based applications,"
datePublished: Sat Jun 17 2023 07:15:10 GMT+0000 (Coordinated Universal Time)
cuid: cliznz1i6001509l9elo34gv5
slug: task-install-and-configure-tomcat-server
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1688402542035/a99ff841-2be8-445f-9ded-cb5ed438db46.jpeg
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1686986067270/840bf2e0-ee14-4df5-8252-9fb0eece600c.png
tags: linux, linux-for-beginners, kodekloud

---

## Problem:

> The `Nautilus` application development team recently finished the beta version of one of their Java-based applications, which they are planning to deploy on one of the app servers in `Stratos DC`. After an internal team meeting, they have decided to use the `tomcat` application server. Based on the requirements mentioned below complete the task:
> 
> a. Install `tomcat` server on `App Server 1` using `yum`.
> 
> b. Configure it to run on port `8086`.
> 
> c. There is a `ROOT.war` file on `Jump host` at location `/tmp`. Deploy it on this tomcat server and make sure the webpage works directly on base URL i.e without specifying any sub-directory anything like this [`http://URL/ROOT`](http://URL/ROOT) .

## Solution:

*<mark><br>Please ensure to review the task instructions carefully and modify the commands according to your specific server, username, and other relevant details.</mark>*

1. ssh into app server1
    
2. Install Tomcat on it
    
    ```plaintext
    sudo yum install tomcat -y
    ```
    
3. Configure Tomcat to run on port 8086. Open the Tomcat configuration file using a text editor. For example:
    
    ```plaintext
    sudo vi /etc/tomcat/server.xml
    ```
    
4. Inside the `server.xml` file, locate the section where the default HTTP connector is defined. It typically looks like this:
    
    ```plaintext
    <Connector port="8086" protocol="HTTP/1.1"
               connectionTimeout="20000"
               redirectPort="8443" />
    ```
    
    Change the `port` attribute value to `8086` and save it.
    
    ```plaintext
    <Connector port="8086" protocol="HTTP/1.1"
               connectionTimeout="20000"
               redirectPort="8443" />
    ```
    
5. Now let's copy `ROOT.war` file from the jump server to this app server1. For that, we need to ssh onto the jump server. You can either open up the new tab from this task editor or just log out from app server1 it automatically gets you to the jump server.
    
    ```plaintext
    scp /tmp/ROOT.war tony@<app-server-1>:/tmp
    ```
    

In step5 remember to input either the IP Address or Hostname of the `app`\-`server` whatever it is according to your task

1. In step 5 we have copied the `ROOT.war` from jump server to app sserver1 in `/tmp` the directory. Move the `ROOT.war` file to the Tomcat `webapps` directory. Run the following commands:
    
    ```plaintext
    sudo mv /tmp/ROOT.war /var/lib/tomcat/webapps/
    ```
    
2. Start or restart the Tomcat service for the changes to take effect. Use the following command:
    
    ```plaintext
    sudo systemctl restart tomcat
    ```
    
    The Tomcat server should now be running on port 8086 with the deployed ROOT web application.
    
3. Verify that the webpage works directly on the base URL.
    
    ```plaintext
    curl -I http://172.16.238.10:8086
    ```
    

References:

[https://stackoverflow.com/questions/18415578/how-to-change-apache-tomcat-web-server-port-number](https://stackoverflow.com/questions/18415578/how-to-change-apache-tomcat-web-server-port-number)

[https://www.digitalocean.com/community/tutorials/how-to-install-apache-tomcat-7-on-centos-7-via-yum](https://www.digitalocean.com/community/tutorials/how-to-install-apache-tomcat-7-on-centos-7-via-yum)