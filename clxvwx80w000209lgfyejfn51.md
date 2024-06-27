---
title: "Task - Troubleshoot Docker Container Issue"
seoTitle: "Troubleshoot Docker Container Issue"
seoDescription: "Task - Troubleshoot Docker Container Issue"
datePublished: Wed Jun 26 2024 14:10:12 GMT+0000 (Coordinated Universal Time)
cuid: clxvwx80w000209lgfyejfn51
slug: task-troubleshoot-docker-container-issue
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1719410935082/aa697ef9-14ee-4151-9e3c-02e12710116f.png
tags: linux, docker, devops, docker-container, kodekloud, kodekloudengineer, kodekloudtasks

---

### Problem:

> An issue has arisen with a static website running in a container named `nautilus` on `App Server 1`. To resolve the issue, investigate the following details:
> 
> 1. Check if the container's volume `/usr/local/apache2/htdocs` is correctly mapped with the host's volume `/var/www/html`.
>     
> 2. Verify that the website is accessible on host port `8080` on `App Server 1`. Confirm that the command `curl`[`http://localhost:8080/`](http://localhost:8080/) works on `App Server 1`.
>     

### Solution:

1. ssh into App Server 1
    
2. Do `docker ps -a` You will see a container named `Nautilus` is in stopped mode.
    
3. Start the container with `docker start nautilus`
    
4. Do `docker ps` and take the container ID.
    
5. Inspect the container with its container ID `docker inspect 3sdede33.` Here you will see the `nautilus` container's details/configuration in the long `JSON` format.
    
    Note :`3sdede33` is the container ID in your case it might be different. So you will get it from the 4th step, use the appropriate container ID.
    
6. After the 5th step, you will see the very long `JSON` format output. To directly go to the Mounts section from JSON use this command `docker inspect 3sdede33 | grep -A 10 -B 10 -i mount.` You will see something like this
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1719410486091/63719fbe-fcd6-4908-a12f-ff2143c0ded1.png align="center")

Here you have to verify whether the local host path and docker path are correctly bound or not. So in my case, it was correct. Mounting is correct.

7. Now, that Mouting is correct we checked it time to check, whether prot binding is correct or not. For that do `docker ps` You will see the "PORTS" column check the if host port is bound with the docker port or not.
    
8. Do `curl`[`http://localhost:8080/`](http://localhost:8080/) If you get a response on the terminal then you have inspected this docker container successfully. Submit the task and enjoy.
    

# About me

Hi My name is Sachin Khamitkar and I am a passionate devops engineer and an Expert Support Engineer. As a DevOps enthusiast and technology fan, I am passionate about automating workflows, optimizing infrastructure, and improving deployment processes. I love sharing insights on cloud strategies, containerization, and continuous delivery. With 6 years of experience in Technical and Application Support, I have a strong foundation in DevOps practices. I excel in root cause analysis, SLA adherence, and enhancing software stability. My skills include log analysis, SQL reporting, and CI/CD pipeline optimization. I have a proven track record in deploying builds, patches, and maintaining production environments. Additionally, I bring expertise in incident, problem, and change management following ITIL standards. If you're as excited about DevOps as I am, let's connect 🌟 me on [LinkedIn](https://www.linkedin.com/in/sachin-khamitkar)🔗💼, [GitHub](https://github.com/sachin-2-github)💻🔗, and [Email](mailto:sachin.bmp@gmail.com)📧 for more tech tips, tutorials, and exciting projects! Let's innovate together and drive the future of DevOps! 🚀👩‍💻💡