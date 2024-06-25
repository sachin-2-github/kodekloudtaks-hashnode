---
title: "Task - Copy File to Docker Container"
seoTitle: "Copy File to Docker Container"
seoDescription: "article to copy which tells how to copy files from host machine to docker."
datePublished: Tue Jun 25 2024 19:19:44 GMT+0000 (Coordinated Universal Time)
cuid: clxusjg1g000809l44mvja4xi
slug: task-copy-file-to-docker-container
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1719343349696/d70fd883-202d-4c05-bd53-50231cb233a1.png
tags: linux, docker, kodekloud, kodekloudengineer, kodekloudtasks

---

# Problem:

> The Nautilus DevOps team possesses confidential data on `App Server 2` in the `Stratos Datacenter`. A container named `ubuntu_latest` is running on the same server.
> 
> Copy an encrypted file `/tmp/nautilus.txt.gpg` from the docker host to the `ubuntu_latest` container located at `/usr/src/`. Ensure the file is not modified during this operation.

## Solution:

*<mark>Please ensure to review the task instructions carefully and modify the commands according to your specific server, username, and other relevant details.</mark>*

1. ssh into appserver2
    
2. Once you are on app server2, execute the below command.
    
    ```plaintext
    docker cp /tmp/nautilus.txt.gpg ubuntu_latest:/usr/src/
    ```
    
    *Note*: From the above command `/tmp/nautilus.txt.gpg` this is the host machine path i.e app server 2 path`. ubuntu_latest` is the container name and `/usr/src/` is the container path.
    
    *References:* [*https://docs.docker.com/reference/cli/docker/container/cp/*](https://docs.docker.com/reference/cli/docker/container/cp/)