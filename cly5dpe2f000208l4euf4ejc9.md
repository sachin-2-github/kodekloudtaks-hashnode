---
title: "Task- File Permission Correction"
seoTitle: "File Permission Correction"
seoDescription: "File Permission Correction, kodekloud"
datePublished: Wed Jul 03 2024 05:09:55 GMT+0000 (Coordinated Universal Time)
cuid: cly5dpe2f000208l4euf4ejc9
slug: task-file-permission-correction
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1719983332271/95ad66a7-cdfd-4125-bb0d-a602a7ba8fbf.png
tags: linux, docker, kodekloud, kodekloudengineer, kodekloudtasks

---

### Problem:

> fter conducting a security audit within the `Stratos DC`, the Nautilus security team discovered misconfigured permissions on critical files. To address this, corrective actions are being taken by the production support team. Specifically, the file named `/etc/hostname` on `Nautilus App 3` server requires adjustments to its Access Control Lists (ACLs) as follows:  
> 
>   
> 
> 1\. The file's user owner and group owner should be set to `root`.  
>   
> 2\. `Others` should possess `read only` permissions on the file.  
>   
> 3\. User `siva` must not have any permissions on the file.  
>   
> 4\. User `rod` should be granted `read only` permission on the file.

*<mark>Please ensure to review the task instructions carefully and modify the commands according to your specific server, username, and other relevant details.</mark>*

### Solution:

1. ssh into `app server3`
    
2. **Set the user owner and group owner to root:**
    
    ```plaintext
    chown root:root /etc/hostname
    ```
    
3. **Set the file permissions to ensure 'others' have read-only access:**
    
    ```plaintext
    chmod 644 /etc/hostname
    ```
    
4. **Ensure user** `siva` has no permissions on the file:
    
    ```plaintext
    setfacl -m u:siva:--- /etc/hostname
    ```
    
5. **Grant user** `rod` read-only permission on the file:
    
    ```plaintext
    setfacl -m u:rod:r-- /etc/hostname
    ```
    

### Explanation:

* **chown root**: Sets the owner and group of the file to `root`.
    
* **chmod 644**: Sets the file permissions so that the owner can read and write, the group can read, and others can read the file.
    
* **setfacl -m u:siva:---**: Modifies the ACL to ensure that the user `siva` has no permissions on the file.
    
* **setfacl -m u:rod:r--**: Modifies the ACL to grant read-only permission to the user `rod`.
    

### Verify the ACLs and Permissions

To verify that the permissions and ACLs have been set correctly, you can use the following commands:

* **Check file ownership and permissions:**
    
    ```plaintext
    bashCopy codels -l /etc/hostname
    ```
    
    You should see `-rw-r--r--` and `root root` as the owner and group.
    
* **Check ACLs on the file:**
    
    ```plaintext
    bashCopy codegetfacl /etc/hostname
    ```
    
    The output should show the ACLs, including the entries for `siva` and `rod`.
    

# About me

Hi I am Sachin Khamitkar and I am a passionate devops engineer and an Expert Support Engineer. As a DevOps enthusiast and technology fan, I am passionate about automating workflows, optimizing infrastructure, and improving deployment processes. I love sharing insights on cloud strategies, containerization, and continuous delivery. With 6 years of experience in Technical and Application Support, I have a strong foundation in DevOps practices. I excel in root cause analysis, SLA adherence, and enhancing software stability. My skills include log analysis, SQL reporting, and CI/CD pipeline optimization. I have a proven track record in deploying builds, patches, and maintaining production environments. Additionally, I bring expertise in incident, problem, and change management following ITIL standards. If you're as excited about DevOps as I am, let's connect 🌟 me on [LinkedIn](https://www.linkedin.com/in/sachin-khamitkar)🔗💼, [GitHub](https://github.com/sachin-2-github)💻🔗, and [Email](mailto:sachin.bmp@gmail.com)📧 for more tech tips, tutorials, and exciting projects! Let's innovate together and drive the future of DevOps! 🚀👩‍💻💡