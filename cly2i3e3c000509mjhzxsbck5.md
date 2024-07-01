---
title: "Task - Data Backup for Developer"
seoTitle: "Data Backup for Developer"
seoDescription: "Data Backup for Developer"
datePublished: Mon Jul 01 2024 04:49:29 GMT+0000 (Coordinated Universal Time)
cuid: cly2i3e3c000509mjhzxsbck5
slug: task-data-backup-for-developer
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1719809362424/1104793b-6cdc-42eb-a19f-cc3cd9332920.jpeg
tags: linux, docker, kodekloud, kodekloudengineer, kodekloudtasks

---

### Problem:

> Within the Stratos DC, the Nautilus storage server hosts a directory named `/data`, serving as a repository for various developers non-confidential data. Developer `ravi` has requested a copy of their data stored in `/data/ravi`. The System Admin team has provided the following steps to fulfill this request:
> 
> a. Create a compressed archive named `ravi.tar.gz` of the `/data/ravi` directory.
> 
> b. Transfer the archive to the `/home` directory on the Storage Server.

*<mark>Please ensure to review the task instructions carefully and modify the commands according to your specific server, username, and other relevant details.</mark>*

### Solution:

1. ssh into the `storageserver`
    
2. ```plaintext
    cd /data/ravi
    ```
    
3. Create `gz` file using the below command
    
    ```plaintext
    sudo tar -czvf ravi.tar.gz /data/ravi
    ```
    
    * `tar`: The command to create and manipulate archive files.
        
    * `-c`: Create a new archive.
        
    * `-z`: Compress the archive using gzip.
        
    * `-v`: Verbosely list files processed.
        
    * `-f`: Specify the filename of the archive.
        
4. Now, we have created a compressed file, Copy the compressed file to the specified location.
    
    ```plaintext
    cp ravi.tar.gz /home/
    ```
    

### Verify:

```plaintext
cd /home
ls -lrt
```

You should see the archive file here in under /`home` directory

# About me:

Hi, I am Sachin Khamitkar and I am a passionate devops engineer and an Expert Support Engineer. As a DevOps enthusiast and technology fan, I am passionate about automating workflows, optimizing infrastructure, and improving deployment processes. I love sharing insights on cloud strategies, containerization, and continuous delivery. With 6 years of experience in Technical and Application Support, I have a strong foundation in DevOps practices. I excel in root cause analysis, SLA adherence, and enhancing software stability. My skills include log analysis, SQL reporting, and CI/CD pipeline optimization. I have a proven track record in deploying builds, patches, and maintaining production environments. Additionally, I bring expertise in incident, problem, and change management following ITIL standards. If you're as excited about DevOps as I am, let's connect 🌟 me on [LinkedIn](https://www.linkedin.com/in/sachin-khamitkar)🔗💼, [GitHub](https://github.com/sachin-2-github)💻🔗, and [Email](mailto:sachin.bmp@gmail.com)📧 for more tech tips, tutorials, and exciting projects! Let's innovate together and drive the future of DevOps! 🚀👩‍💻💡