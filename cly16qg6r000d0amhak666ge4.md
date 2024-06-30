---
title: "Task- Linux User Data Transfer"
seoTitle: "Linux User Data Transfer
"
seoDescription: "Linux User Data Transfer
"
datePublished: Sun Jun 30 2024 06:43:43 GMT+0000 (Coordinated Universal Time)
cuid: cly16qg6r000d0amhak666ge4
slug: task-linux-user-data-transfer
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1719729746972/74389151-9102-46e8-9c7b-9aa7a073cb28.avif
tags: linux, devops, devops-articles, kodekloud, kodekloudengineer, kodekloudtasks

---

### Problem:

> Due to an accidental data mix-up, user data was unintentionally mingled on Nautilus `App Server 2` at the `/home/usersdata` location by the Nautilus production support team in Stratos DC. To rectify this, specific user data needs to be filtered and relocated. Here are the details:  
> 
>   
> 
> Locate all files (excluding directories) owned by user `john` within the `/home/usersdata` directory on `App Server 2`. Copy these files while preserving the directory structure to the `/blog` directory.

*<mark>Please ensure to review the task instructions carefully and modify the commands according to your specific server, username, and other relevant details.</mark>*

### Solution:

1. ssh into `app sever2`
    
2. Use the `find` command to locate all files owned by `john` in the `/home/usersdata` directory, excluding directories.
    
    ```plaintext
    find /home/usersdata -type f -user john
    ```
    
3. Use the `find` command combined with `cp --parents` to copy the files while preserving the directory structure.
    
    ```plaintext
    find /home/usersdata -type f -user john -exec cp --parents {} /blog \;
    ```
    
    * `/home/usersdata`: Directory to search in.
        
    * `-type f`: Locate files (excluding directories).
        
    * `-user john`: Find files owned by the user `john`.
        
    * `-exec cp --parents {} /blog \;`: For each file found, execute the `cp --parents` command to copy the file to the `/blog` directory, preserving the directory structure.
        
    

# About me

Hi I am Sachin Khamitkar and I am a passionate devops engineer and an Expert Support Engineer. As a DevOps enthusiast and technology fan, I am passionate about automating workflows, optimizing infrastructure, and improving deployment processes. I love sharing insights on cloud strategies, containerization, and continuous delivery. With 6 years of experience in Technical and Application Support, I have a strong foundation in DevOps practices. I excel in root cause analysis, SLA adherence, and enhancing software stability. My skills include log analysis, SQL reporting, and CI/CD pipeline optimization. I have a proven track record in deploying builds, patches, and maintaining production environments. Additionally, I bring expertise in incident, problem, and change management following ITIL standards. If you're as excited about DevOps as I am, let's connect 🌟 me on [LinkedIn](https://www.linkedin.com/in/sachin-khamitkar)🔗💼, [GitHub](https://github.com/sachin-2-github)💻🔗, and [Email](mailto:sachin.bmp@gmail.com)📧 for more tech tips, tutorials, and exciting projects! Let's innovate together and drive the future of DevOps! 🚀👩‍💻💡