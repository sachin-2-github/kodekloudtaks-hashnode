---
title: "Task - Git Install and Create Bare Repository"
seoTitle: "Task - Git Install and Create Bare Repository"
seoDescription: "Task - Git Install and Create Bare Repository"
datePublished: Mon Jul 10 2023 13:02:42 GMT+0000 (Coordinated Universal Time)
cuid: cljwvikto000209mgdi4606q5
slug: task-git-install-and-create-bare-repository
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1688990427898/fc06fe2b-3d0a-4a8a-b563-260581d256de.jpeg
tags: kodekloud

---

## Problem:

> The `Nautilus` development team shared requirements with the DevOps team regarding new application development.—specifically, they want to set up a `Git` repository for that project. Create a `Git` repository on Storage server in `Stratos DC` as per details given below:
> 
> Install `git` package using `yum` on `Storage server.`
> 
> After that create a `bare` repository `/opt/news.git` (make sure to use exact name).

## Solution:

*<mark>Please ensure to review the task instructions carefully and modify the commands according to your specific server, username, and other relevant details.</mark>*

1. ssh into the storage server.
    
2. Install the git package:
    
    ```plaintext
    sudo yum install git
    ```
    
3. Create the directory for the bare repository:
    
    ```plaintext
    sudo mkdir /opt/news.git
    ```
    
4. Change to the directory:
    
    ```plaintext
    cd /opt/news.git
    ```
    
5. Initialize the bare repository:
    
    ```plaintext
    sudo git init --bare
    ```
    

## Reference :

[https://docshield.kofax.com/RPA/en\_US/11.0.0\_qrvv5i5e1a/help/BestPracticesHelp/rpa\_rlm\_best\_practices/c\_initialize\_bare.html](https://docshield.kofax.com/RPA/en_US/11.0.0_qrvv5i5e1a/help/BestPracticesHelp/rpa_rlm_best_practices/c_initialize_bare.html)

# **About me**

Hi My name is Sachin Khamitkar and I am a passionate devops engineer and an Expert Support Engineer. As a DevOps enthusiast and technology fan, I am passionate about automating workflows, optimizing infrastructure, and improving deployment processes. I love sharing insights on cloud strategies, containerization, and continuous delivery. With 6 years of experience in Technical and Application Support, I have a strong foundation in DevOps practices. I excel in root cause analysis, SLA adherence, and enhancing software stability. My skills include log analysis, SQL reporting, and CI/CD pipeline optimization. I have a proven track record in deploying builds, patches, and maintaining production environments. Additionally, I bring expertise in incident, problem, and change management following ITIL standards. If you're as excited about DevOps as I am, let's connect 🌟 me on [**LinkedIn**🔗💼,](https://www.linkedin.com/in/sachin-khamitkar) [**Gi**](https://github.com/sachin-2-github)[**tHub**💻🔗](https://www.linkedin.com/in/sachin-khamitkar), an[d **Emai**](https://github.com/sachin-2-github)[**l**📧](mailto:sachin.bmp@gmail.com) for m[ore t](mailto:sachin.bmp@gmail.com)ech tips, tutorials, and exciting projects! Let's innovate together and drive the future of DevOps! 🚀👩‍💻💡