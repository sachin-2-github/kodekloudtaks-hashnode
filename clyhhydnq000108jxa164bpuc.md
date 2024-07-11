---
title: "Task - Firewall Configuration"
seoTitle: "Task - Firewall Configuration
"
seoDescription: "Task - Firewall Configuration
kdoekloud"
datePublished: Thu Jul 11 2024 16:42:07 GMT+0000 (Coordinated Universal Time)
cuid: clyhhydnq000108jxa164bpuc
slug: task-firewall-configuration
tags: kodekloud, kodekloudengineer, kodekloudtasks

---

### Problem:

> The `Nautilus` system admins team has rolled out a web UI application for their backup utility on the `Nautilus backup server` within the `Stratos Datacenter`. This application operates on port `5000`, and `firewalld` is active on the server. To meet operational needs, the following requirements have been identified:  
> 
>   
> 
> Allow all incoming connections on port `5000/tcp`. Ensure the zone is set to `public`.

### Solution:

1. **ssh into** `backup server`
    
2. **Allow incoming connections on port 5000/tcp:**
    
    ```apache
    sudo firewall-cmd --zone=public --add-port=5000/tcp --permanent
    ```
    
3. **Reload the firewall to apply the changes:**
    
    ```apache
    sudo firewall-cmd --reload
    ```
    
4. **Verify the changes to ensure the port is open:**
    
    ```apache
    sudo firewall-cmd --zone=public --list-ports
    ```
    

# About me:

Hi, I am Sachin Khamitkar, a Passionate DevOps Engineer and an Expert Support Engineer. As a DevOps enthusiast and technology fan, I am passionate about automating workflows, optimizing infrastructure, and improving deployment processes. I love sharing insights on cloud strategies, containerization, and continuous delivery. With 6 years of experience in Technical and Application Support, I have a strong foundation in DevOps practices. I excel in root cause analysis, SLA adherence, and enhancing software stability. My skills include log analysis, SQL reporting, and CI/CD pipeline optimization. I have a proven track record in deploying builds, patches, and maintaining production environments. Additionally, I bring expertise in incident, problem, and change management following ITIL standards. If you're as excited about DevOps as I am, let's connect 🌟 me on [LinkedIn](https://www.linkedin.com/in/sachin-khamitkar)🔗💼, [Gitlab](https://gitlab.com/sachin-2-github)💻🔗, and [Email](mailto:sachin.bmp@gmail.com)📧 for more tech tips, tutorials, and exciting projects! Let's innovate together and drive the future of DevOps! 🚀👩‍💻💡