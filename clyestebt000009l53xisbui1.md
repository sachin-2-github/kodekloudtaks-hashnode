---
title: "Task - Default GUI Boot Configuration"
seoTitle: "Default GUI Boot Configuration"
seoDescription: "Default GUI Boot Configuration"
datePublished: Tue Jul 09 2024 19:22:52 GMT+0000 (Coordinated Universal Time)
cuid: clyestebt000009l53xisbui1
slug: task-default-gui-boot-configuration
tags: kodekloud, kodekloudengineer, kodekloudtasks

---

### Problem:

> With the installation of new tools on the app servers within the `Stratos Datacenter`, certain functionalities now necessitate graphical user interface (GUI) access.
> 
> Adjust the `default runlevel` on all App servers in `Stratos Datacenter` to enable GUI booting by default. It's imperative not to initiate a server reboot after completing this task.

*<mark>Please ensure to review the task instructions carefully and modify the commands according to your specific server, username, and other relevant details.</mark>*

### Solution:

ssh into all `app servers` and repeat the steps.

1. Edit the `systemd` configuration to change the default target (`runlevel`):
    
    ```plaintext
    sudo systemctl set-default graphical.target
    ```
    
2. Verify: Check the current target to ensure it's set correctly:
    
    ```plaintext
    sudo systemctl get-default
    ```
    

# About me:

Hi, I am Sachin Khamitkar, a passionate devops engineer and an Expert Support Engineer. As a DevOps enthusiast and technology fan, I am passionate about automating workflows, optimizing infrastructure, and improving deployment processes. I love sharing insights on cloud strategies, containerization, and continuous delivery. With 6 years of experience in Technical and Application Support, I have a strong foundation in DevOps practices. I excel in root cause analysis, SLA adherence, and enhancing software stability. My skills include log analysis, SQL reporting, and CI/CD pipeline optimization. I have a proven track record in deploying builds, patches, and maintaining production environments. Additionally, I bring expertise in incident, problem, and change management following ITIL standards. If you're as excited about DevOps as I am, let's connect 🌟 me on [LinkedIn](https://www.linkedin.com/in/sachin-khamitkar)🔗💼, [GitHub](https://github.com/sachin-2-github)💻🔗, and [Email](mailto:sachin.bmp@gmail.com)📧 for more tech tips, tutorials, and exciting projects! Let's innovate together and drive the future of DevOps! 🚀👩‍💻💡