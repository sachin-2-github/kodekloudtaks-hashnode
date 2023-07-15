---
title: "Task - Puppet Create Symlinks"
seoTitle: "Task - Puppet Create Symlinks"
seoDescription: "Task - Puppet Create Symlinks"
datePublished: Sat Jul 15 2023 12:30:11 GMT+0000 (Coordinated Universal Time)
cuid: clk3zk0ie000e09jo5djte7nn
slug: task-puppet-create-symlinks
tags: kodekloud

---

## Problem:

> Some directory structure in the Stratos Datacenter needs to be changed, there is a directory that needs to be linked to the default Apache document root. We need to accomplish this task using Puppet, as per the instructions given below:
> 
>   
> 
> Create a puppet programming file `demo.pp` under `/etc/puppetlabs/code/environments/production/manifests` directory on puppet master node i.e on `Jump Server`. Within that define a class `symlink` and perform below mentioned tasks:
> 
> 1. Create a `symbolic link` through puppet programming code. The source path should be `/opt/dba` and destination path should be `/var/www/html` on Puppet agents 2 i.e on `App Servers 2`.
>     
> 2. Create a blank file `blog.txt` under `/opt/dba` directory on puppet agent 2 nodes i.e on `App Servers 2`.
>     
> 
> `Notes:` :- Please make sure to run the puppet agent test using `sudo` on agent nodes, otherwise you can face certificate issues. In that case you will have to clean the certificates first and then you will be able to run the puppet agent test.
> 
> :- Before clicking on the `Check` button please make sure to verify puppet server and puppet agent services are up and running on the respective servers, also please make sure to run puppet agent test to apply/test the changes manually first.
> 
> :- Please note that once lab is loaded, the puppet server service should start automatically on puppet master server, however it can take upto 2-3 minutes to start.

## Solution:

*<mark>Please ensure to review the task instructions carefully and modify the commands according to your specific server, username, and other relevant details.</mark>*

1. Navigate to `/etc/puppetlabs/code/environments/production/manifests` path and create `demo.pp` on the `jump-server`
    
    ```plaintext
    cd /etc/puppetlabs/code/environments/production/manifests
    sudo touch demo.pp
    ```
    
2. Now add this code to `demo.pp` file and save it.
    
    ```plaintext
    
    node 'stapp02.stratos.xfusioncorp.com' {
      class symlink {
        file { '/var/www/html':
          ensure => 'link',
          target => '/opt/dba',
        }
    
        file { '/opt/dba/blog.txt':
          ensure  => 'file',
          content => '',
        }
      }
    
      include symlink
    }
    ```
    
3. Then execute this command on the Jump server only.
    
    ```plaintext
    sudo puppet parser validate demo.pp
    ```
    
4. Now ssh into `app-server2` & Execute this command.
    
    ```plaintext
    sudo puppet agent -tv
    ```
    
    This command will link `/var/www/html` to `/opt/dba/blog.txt`
    
5. Finally, check if the link is working properly and pointing to `blog.txt` or not`app-server2`
    
    ```plaintext
    ll /var/www/html
    ```