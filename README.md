# 🚀 Java CI/CD Pipeline with Jenkins, Docker, Docker Hub & Kubernetes

![Java](https://img.shields.io/badge/Java-17+-orange?logo=openjdk)
![Maven](https://img.shields.io/badge/Maven-Build-red?logo=apachemaven)
![Jenkins](https://img.shields.io/badge/Jenkins-CI%2FCD-blue?logo=jenkins)
![Docker](https://img.shields.io/badge/Docker-Containerization-blue?logo=docker)
![Docker Hub](https://img.shields.io/badge/Docker%20Hub-Registry-2496ED?logo=docker)
![Kubernetes](https://img.shields.io/badge/Kubernetes-Orchestration-326CE5?logo=kubernetes)
![AWS](https://img.shields.io/badge/AWS-EC2-orange?logo=amazonaws)
![GitHub](https://img.shields.io/badge/GitHub-Source%20Control-black?logo=github)

> A complete hands-on DevOps CI/CD project demonstrating how a Java application moves from GitHub source code through Jenkins, Maven, Docker, Docker Hub and finally into a Kubernetes cluster running on AWS EC2.

---

# 📌 Project Overview

This project implements an end-to-end CI/CD pipeline for a Java application.

The development environment is a **Windows PC** running:

* VS Code
* Git
* Docker Desktop
* Jenkins container

Jenkins performs the CI/CD automation.

Maven build and test operations are executed using a **Docker-based Maven agent**, rather than requiring Maven to be permanently installed inside the Jenkins controller container.

The final Docker image is pushed to Docker Hub and deployed to a Kubernetes cluster running on AWS EC2.

---

# 🏗️ Target Architecture

```text
                         WINDOWS PC
┌─────────────────────────────────────────────────────────────┐
│                                                             │
│   VS Code                                                   │
│      │                                                      │
│      │ git push                                             │
│      ▼                                                      │
│   ┌───────────────┐                                         │
│   │    GitHub     │                                         │
│   │ Source Code   │
```
