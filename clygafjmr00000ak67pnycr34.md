---
title: "Task - Timezone Alignment"
seoTitle: "Timezone Alignment
"
seoDescription: "Timezone Alignment
kdoekloud tasks"
datePublished: Wed Jul 10 2024 20:23:45 GMT+0000 (Coordinated Universal Time)
cuid: clygafjmr00000ak67pnycr34
slug: task-timezone-alignment
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1720642978730/59d0135e-a79f-4c02-b8fb-aa1ae0d62cee.png
tags: kodekloud, kodekloudengineer, kodekloudtasks

---

### Problem:

> n the daily standup, it was noted that the timezone settings across the `Nautilus Application Servers` in the `Stratos Datacenter` are inconsistent with the local datacenter's timezone, currently set to `America/Argentina/San_Luis`.  
> 
>   
> 
> Synchronize the timezone settings to match the local datacenter's timezone (`America/Argentina/San_Luis`).

*<mark>Please ensure to review the task instructions carefully and modify the commands according to your specific server, username, and other relevant details.</mark>*

### Solution:

ssh into all `app servers` and repeat the steps.

1. First, check the current timezone setting on your servers:
    

```plaintext
timedatectl
```

2. Change the timezone to America/Argentina/San\_Luis:
    

```plaintext
sudo timedatectl set-timezone America/Argentina/San_Luis
```

3. Verify that the timezone has been updated correctly:
    

```plaintext
timedatectl
```

# About me:

Hi, I am Sachin Khamitkar, a passionate devops engineer and an Expert Support Engineer. As a DevOps enthusiast and technology fan, I am passionate about automating workflows, optimizing infrastructure, and improving deployment processes. I love sharing insights on cloud strategies, containerization, and continuous delivery. With 6 years of experience in Technical and Application Support, I have a strong foundation in DevOps practices. I excel in root cause analysis, SLA adherence, and enhancing software stability. My skills include log analysis, SQL reporting, and CI/CD pipeline optimization. I have a proven track record in deploying builds, patches, and maintaining production environments. Additionally, I bring expertise in incident, problem, and change management following ITIL standards. If you're as excited about DevOps as I am, let's connect 🌟 me on [LinkedIn](https://www.linkedin.com/in/sachin-khamitkar)🔗💼, [Gitlab](https://gitlab.com/sachin-2-github)💻🔗, and [Email](mailto:sachin.bmp@gmail.com)📧 for more tech tips, tutorials, and exciting projects! Let's innovate together and drive the future of DevOps! 🚀👩‍💻💡