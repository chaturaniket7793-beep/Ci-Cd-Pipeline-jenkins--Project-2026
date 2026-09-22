# Java CI/CD with Jenkins, Docker & Kubernetes

A simple end-to-end DevOps project that builds a Java application with Maven, creates a Docker image, pushes it to Docker Hub, and deploys it to Kubernetes on AWS EC2.

## Architecture
<img width="946" height="627" alt="image" src="https://github.com/user-attachments/assets/858c155e-97b9-4d5d-afc2-b11779ea69a7" />



```text
VS Code
   │
   │ git push
   ▼
GitHub
   │
   ▼
Jenkins
(Docker Desktop)
   │
   ├── Maven Build
   ├── Maven Test
   ├── Docker Build
   └── Docker Push
          │
          ▼
      Docker Hub
          │
          ▼
       AWS EC2
     Kubernetes
          │
      ┌───┴───┐
      ▼       ▼
    Pod 1   Pod 2
      └───┬───┘
          ▼
       Service
       NodePort
          │
          ▼
       Browser
```

## Technologies

* Java 17
* Maven
* Git & GitHub
* Jenkins
* Docker Desktop
* Docker Hub
* Kubernetes
* AWS EC2

## Project Structure

```text
java-jenkins-docker/
│
├── src/
├── k8s/
│   └── deployment.yaml
├── pom.xml
├── Dockerfile
├── Jenkinsfile
└── README.md
```

## CI/CD Flow

```text
Git Push
   ↓
Jenkins
   ↓
Maven Build
   ↓
Maven Test
   ↓
Docker Build
   ↓
Docker Hub
   ↓
Kubernetes
   ↓
Pods
   ↓
Service
   ↓
Browser
```

## Maven

Build:

```bash
mvn clean package
```

Test:

```bash
mvn test
```

## Docker

Build:

```bash
docker build -t YOUR_DOCKER_USERNAME/java-jenkins-docker:latest .
```

Run:

```bash
docker run java-jenkins-docker:latest
```

## Kubernetes

The `k8s/deployment.yaml` file contains both:

* Deployment
* Service

Apply both with one command:

```bash
kubectl apply -f k8s/deployment.yaml
```

Check Pods:

```bash
kubectl get pods
```

Check Service:

```bash
kubectl get svc
```

## Browser Access

The Kubernetes Service uses **NodePort**.

```text
Browser
   ↓
http://EC2-PUBLIC-IP:NODEPORT
   ↓
Kubernetes Service
   ↓
Pod
   ↓
Java Application
```

Example:

```text
http://<EC2-PUBLIC-IP>:30080
```

Make sure the EC2 Security Group allows the NodePort.

## Jenkins Pipeline

The Jenkins pipeline will perform:

```text
Checkout
   ↓
Maven Build
   ↓
Maven Test
   ↓
Docker Build
   ↓
Docker Push
   ↓
Kubernetes Deploy
```

## Jenkins Credentials

Store credentials in Jenkins, not in GitHub.

```text
Docker Hub credentials
Kubernetes credentials
```

Never commit passwords, tokens, or kubeconfig files.

## Project Goal

The final goal is:

```text
GitHub
   ↓
Jenkins
   ↓
Maven
   ↓
Docker
   ↓
Docker Hub
   ↓
AWS EC2
   ↓
Kubernetes
   ↓
Pod 1 + Pod 2
   ↓
NodePort
   ↓
Browser
```

This project is for hands-on DevOps and CI/CD practice.
