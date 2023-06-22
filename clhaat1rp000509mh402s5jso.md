---
title: "Task 31- Install the Telnet package"
datePublished: Fri May 05 2023 08:32:38 GMT+0000 (Coordinated Universal Time)
cuid: clhaat1rp000509mh402s5jso
slug: task-31-install-the-telnet-package

---

  

Problem:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1683274282734/4cf4e498-7496-41e4-bd57-ea0ce14c8f21.png align="center")

Solution:

ssh into all app servers and Follow these steps

1. sudo yum update -y
    
2. sudo yum install telnet -y
    

Note: Check whether the Telenet is installed or not with this command

```plaintext
telnet localhost 22
```