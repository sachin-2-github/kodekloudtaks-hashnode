---
title: "Task - Puppet Manage Services"
seoTitle: "Task - Puppet Manage Services"
seoDescription: "Task - Puppet Manage Services"
datePublished: Wed Jul 12 2023 10:32:46 GMT+0000 (Coordinated Universal Time)
cuid: cljzl1gmg000a09l790dx0twv
slug: task-puppet-manage-services
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1689157926409/2618b8ee-b602-4fd4-9c06-b3c02992bf6e.png
tags: kodekloud

---

## Problem:

> New packages need to be installed on some of the app servers in `Stratos Datacenter`. The Nautilus DevOps team has decided to install the same using Puppet. Since `jump host` is already configured to run as Puppet master server and all app servers are already configured to work as puppet agent nodes, we need to create the required manifests on the Puppet master server so that it can be applied on the required Puppet agent node. Please find more details about the task below.
> 
> Create a Puppet programming file `cluster.pp` under `/etc/puppetlabs/code/environments/production/manifests` directory on `master` node i.e `Jump Host` to perform the below given tasks.
> 
> 1. Install package `httpd` using puppet `package` resource and start its service using puppet `service` resource on Puppet agent node 2 i.e `App Server 2`.
>     
> 
> `Notes:` :- Please make sure to run the puppet agent test using `sudo` on agent nodes, otherwise you can face certificate issues. In that case you will have to clean the certificates first and then you will be able to run the puppet agent test.
> 
> :- Before clicking on the `Check` button please make sure to verify puppet server and puppet agent services are up and running on the respective servers, also please make sure to run puppet agent test to apply/test the changes manually first.
> 
> :- Please note that once lab is loaded, the puppet server service should start automatically on puppet master server, however it can take upto 2-3 minutes to start.

## Solution:

*<mark>Please ensure to review the task instructions carefully and modify the commands according to your specific server, username, and other relevant details.</mark>*

1. Navigate to `/etc/puppetlabs/code/environments/production/manifests` path and create `cluster.pp` on the `jump-server`
    
    ```plaintext
    cd /etc/puppetlabs/code/environments/production/manifests
    sudo touch cluster.pp
    ```
    
2. Now add this code to `cluster.pp` file and save it.
    
    ```plaintext
    
    node 'stapp02.stratos.xfusioncorp.com' {
      package { 'httpd':
        ensure => installed,
      }
    
      service { 'httpd':
        ensure => running,
        enable => true,
      }
    }
    ```
    
3. Then execute this command on the Jump server only.
    
    ```plaintext
    sudo puppet parser validate cluster.pp
    ```
    
4. Now ssh into `app-server2` & Execute this command.
    
    ```plaintext
    sudo puppet agent -tv
    ```
    
    This command will install the package. We mentioned in the `cluster.pp`
    
5. Finally, check the installed package in our `thttpd` is running or not on `app-server2`
    
    ```plaintext
    sudo systemctl status httpd
    ```