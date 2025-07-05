# 🐳 Docker Hello-Env Project

This project demonstrates a simple Docker container that prints personalized environment messages. It includes creating a Dockerfile, passing environment variables, building an image, and running a container — all from scratch on an AWS EC2 instance (Ubuntu).

---

## ✅ Project Goals

- Understand Docker basics and Dockerfile structure  
- Use `ENV` to set environment variables  
- Write and run a basic shell script in a container  
- Deploy on an EC2 instance

---

## 🛠 Tools & Services Used

- Docker (installed on EC2 Ubuntu)
- AWS EC2 (Ubuntu instance)
- Shell Scripting (`app.sh`)
- GitHub (for version control)

---

## 🧭 Step-by-Step Implementation

### 1️⃣ EC2 Setup
- Created a free-tier Ubuntu EC2 instance
- SSH'd into the instance using `.pem` file

### 2️⃣ Docker Installation
- Installed Docker using `apt` commands
- Verified with `docker --version`

### 3️⃣ Project Structure

```bash
hello-env/
├── Dockerfile
└── app.sh
```
### 4️⃣ Write the Shell Script
```bash#!/bin/bash
echo "hello, $user_name"
echo "you are working in $env_mode environment"
```
- Made the script executable (if needed)
 ```bash
 chmod +x app.sh
  ```
### 5️⃣ Create Dockerfile
- Wrote a simple Dockerfile to define how the image is built
   ```bash
  FROM ubuntu:20.04

  ENV user_name="prudvi"
  ENV env_mode="development"

  ORKDIR /app

   OPY app.sh .

  RUN apt-get update && apt-get install -y bash

  CMD ["bash", "app.sh"]
    ```
### 6️⃣ Build Docker Image
  - Ran the following command to build the Docker image
    ```bash
    docker build -t hello-env .
    ```
### 7️⃣ Run Docker Container
  ```bash
  docker run hello-env
  ```
### 🖨️ Output:
```bash
hello, prudvi
you are working in development environment
```
---

### 💥 Challenges Faced
1. Dockerfile Naming Confusion :
   
   Initially, I named the file as Docker-file instead of Dockerfile, which caused build failures. Docker looks specifically for a file named Dockerfile (case-sensitive, no extension).
   
2. ENV Syntax Mistake :
   
   I used spaces while setting environment variables in the Dockerfile, like:  
   ENV user_name = "prudvi"  
   Correct syntax: ENV user_name="prudvi" (no spaces around =)
3. Permission Denied While SSH :
   
   Faced issues with SSH due to using the wrong username.  
   Remember: For Ubuntu EC2 instances, the username is always ubuntu.
---
### 📘 Key Takeaways
- Understood how to create and use a Dockerfile
- Learned to pass environment variables to containers
- Practiced Docker workflow from EC2 (build → run)
- Solved common beginner mistakes in Docker and SSH
  
----

   

  
    


    













