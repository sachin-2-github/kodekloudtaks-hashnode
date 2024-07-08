---
title: "Task -  String Replacement"
seoTitle: "String Replacement"
seoDescription: "String Replacement, kodekloud tasks"
datePublished: Mon Jul 08 2024 13:43:20 GMT+0000 (Coordinated Universal Time)
cuid: clyd18wf300000amndcj8d6ob
slug: task-string-replacement
tags: kodekloud, kodekloudengineer, kodekloudtasks

---

### Problem:

> Within the Stratos DC, the backup server holds template XML files crucial for the Nautilus application. Before utilization, these files require valid data insertion. As part of routine maintenance, system admins at `xFusionCorp Industries` employ string and file manipulation commands.  
> 
>   
> 
> Your task is to substitute all occurrences of the string `About` with `Cloud` within the XML file located at `/root/nautilus.xml` on the backup serv

*<mark>Please ensure to review the task instructions carefully and modify the commands according to your specific server, username, and other relevant details.</mark>*

### Solution:

1. ssh into `backup` server
    
2. To substitute all occurrences of the string "About" with "Cloud" within the XML file located at `/root/nautilus.xml`, you can use the `sed` command. Here is how you can do it:
    
    ```plaintext
    sed -i 's/About/Cloud/g' /root/nautilus.xml
    ```
    
    ### Explanation:
    
    * `sed`: Stream editor for filtering and transforming text.
        
    * `-i`: Option to edit the file in place.
        
    * `s/About/Cloud/g`: `s` is the substitute command. It replaces occurrences of the string "About" with "Cloud". The `g` at the end stands for "global", meaning it will replace all occurrences in each line.
        
    * `/root/nautilus.xml`: The path to the file where the substitution will take place.
        

Hi, I am Sachin Khamitkar, a passionate devops engineer and an Expert Support Engineer. As a DevOps enthusiast and technology fan, I am passionate about automating workflows, optimizing infrastructure, and improving deployment processes. I love sharing insights on cloud strategies, containerization, and continuous delivery. With 6 years of experience in Technical and Application Support, I have a strong foundation in DevOps practices. I excel in root cause analysis, SLA adherence, and enhancing software stability. My skills include log analysis, SQL reporting, and CI/CD pipeline optimization. I have a proven track record in deploying builds, and patches and maintaining production environments. Additionally, I bring expertise in incident, problem, and change management following ITIL standards. If you're as excited about DevOps as I am, let's connect 🌟 me on [LinkedIn](https://www.linkedin.com/in/sachin-khamitkar)🔗💼, [GitHub](https://github.com/sachin-2-github)💻🔗, and [Email](mailto:sachin.bmp@gmail.com)📧 for more tech tips, tutorials, and exciting projects! Let's innovate together and drive the future of DevOps! 🚀👩‍💻💡