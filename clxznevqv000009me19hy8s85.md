---
title: "Task - Service User Creation without Home Directory"
seoTitle: "Service User Creation without Home Directory
"
seoDescription: "Service User Creation without Home Directory
"
datePublished: Sat Jun 29 2024 04:55:04 GMT+0000 (Coordinated Universal Time)
cuid: clxznevqv000009me19hy8s85
slug: task-service-user-creation-without-home-directory
tags: linux, kodekloud, kodekloudengineer, kodekloudtasks

---

### Problem:

> In response to the latest tool implementation at `xFusionCorp Industries`, the system admins require the creation of a service user account. Here are the specifics:
> 
> Create a user named `ravi` in `App Server 3` without a home directory

*<mark>Please ensure to review the task instructions carefully and modify the commands according to your specific server, username, and other relevant details.</mark>*

### Solution:

1. ssh into `app sever3`
    
2. Use the `useradd` command with the `-M` option to create a user without a home directory
    
    ```plaintext
    sudo useradd -M ravi
    ```
    
    ### Verify:
    
    1. Alternatively, you can list the `/home` directory to confirm the new user doesn't have a home directory.
        
        ```plaintext
        ls /home
        ```
        
    2. To verify if a user is created or noted use.
        
        ```plaintext
        id ravi
        ```
        

# About me

Hi I am Sachin Khamitkar and I am a passionate devops engineer and an Expert Support Engineer. As a DevOps enthusiast and technology fan, I am passionate about automating workflows, optimizing infrastructure, and improving deployment processes. I love sharing insights on cloud strategies, containerization, and continuous delivery. With 6 years of experience in Technical and Application Support, I have a strong foundation in DevOps practices. I excel in root cause analysis, SLA adherence, and enhancing software stability. My skills include log analysis, SQL reporting, and CI/CD pipeline optimization. I have a proven track record in deploying builds, patches, and maintaining production environments. Additionally, I bring expertise in incident, problem, and change management following ITIL standards. If you're as excited about DevOps as I am, let's connect 🌟 me on [LinkedIn](https://www.linkedin.com/in/sachin-khamitkar)🔗💼, [GitHub](https://github.com/sachin-2-github)💻🔗, and [Email](mailto:sachin.bmp@gmail.com)📧 for more tech tips, tutorials, and exciting projects! Let's innovate together and drive the future of DevOps! 🚀👩‍💻💡