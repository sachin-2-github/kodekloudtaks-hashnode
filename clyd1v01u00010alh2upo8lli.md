---
title: "Task - Restrict Cron Access"
seoTitle: "Restrict Cron Access"
seoDescription: "Restrict Cron Access"
datePublished: Mon Jul 08 2024 14:00:31 GMT+0000 (Coordinated Universal Time)
cuid: clyd1v01u00010alh2upo8lli
slug: task-restrict-cron-access
tags: kodekloud, kodekloudengineer, kodekloudtasks, kodekloud-coupons

---

### Problem:

> In alignment with security compliance standards, the Nautilus project team has opted to impose restrictions on crontab access. Specifically, only designated users will be permitted to create or update cron jobs.
> 
> Configure crontab access on `App Server 3` as follows: Allow crontab access to `mark` user while denying access to the `eric` user.

*<mark>Please ensure to review the task instructions carefully and modify the commands according to your specific server, username, and other relevant details.</mark>*

### Solution:

1. ssh into `App server3`
    
2. Create 2 file `cron.allow` and `corn.deny` under /etc
    
    ```plaintext
    sudo touch /etc/cron.allow
    sudo touch /etc/cron.deny
    ```
    
3. Add mark user in `cron.allow` file, add Eric in `cron.deny` file.
    
    ```plaintext
    sudo echo "marc" >> /etc/cron.allow
    sudo echo "eric" >> /etc/cron.deny
    ```
    
    *Note: 3rd step can be done using any file editor like* `vi` *or* `nano` *too.*
    

# About me:

Hi, I am Sachin Khamitkar, a passionate devops engineer and an Expert Support Engineer. As a DevOps enthusiast and technology fan, I am passionate about automating workflows, optimizing infrastructure, and improving deployment processes. I love sharing insights on cloud strategies, containerization, and continuous delivery. With 6 years of experience in Technical and Application Support, I have a strong foundation in DevOps practices. I excel in root cause analysis, SLA adherence, and enhancing software stability. My skills include log analysis, SQL reporting, and CI/CD pipeline optimization. I have a proven track record in deploying builds, patches, and maintaining production environments. Additionally, I bring expertise in incident, problem, and change management following ITIL standards. If you're as excited about DevOps as I am, let's connect 🌟 me on [LinkedIn](https://www.linkedin.com/in/sachin-khamitkar)🔗💼, [GitHub](https://github.com/sachin-2-github)💻🔗, and [Email](mailto:sachin.bmp@gmail.com)📧 for more tech tips, tutorials, and exciting projects! Let's innovate together and drive the future of DevOps! 🚀👩‍💻💡