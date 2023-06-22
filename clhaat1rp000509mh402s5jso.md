---
title: "Task 31- Install the Telnet package"
seoDescription: "Install the Telnet package"
datePublished: Fri May 05 2023 08:32:38 GMT+0000 (Coordinated Universal Time)
cuid: clhaat1rp000509mh402s5jso
slug: task-31-install-the-telnet-package
tags: linux, kodekloud

---

Problem:

> As per new application requirements shared by the `Nautilus` project development team, several new packages need to be installed on all app servers in `Stratos Datacenter`. Most of them are completed except for `telnet`
> 
> Therefore, install the `telnet` package on all `app-servers`

Solution:

ssh into all app servers and Follow these steps

1. sudo yum update -y
    
2. sudo yum install telnet -y
    

Note: Check whether the Telenet is installed or not with this command

```plaintext
telnet localhost 22
```