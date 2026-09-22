# 🚀 Java CI/CD Pipeline with Jenkins, Docker, Docker Hub & Kubernetes

![Java](https://img.shields.io/badge/Java-17+-orange?logo=openjdk)
![Maven](https://img.shields.io/badge/Maven-Build-red?logo=apachemaven)
![Jenkins](https://img.shields.io/badge/Jenkins-CI/CD-blue?logo=jenkins)
![Docker](https://img.shields.io/badge/Docker-Containerization-blue?logo=docker)
![Docker Hub](https://img.shields.io/badge/Docker%20Hub-Registry-2496ED?logo=docker)
![Kubernetes](https://img.shields.io/badge/Kubernetes-Deployment-326CE5?logo=kubernetes)
![AWS](https://img.shields.io/badge/AWS-EC2-orange?logo=amazonaws)
![GitHub](https://img.shields.io/badge/GitHub-Source%20Control-black?logo=github)

> **A complete end-to-end CI/CD implementation demonstrating how a Java application moves from source code to automated testing, Docker containerization, Docker Hub image publishing, and Kubernetes deployment on AWS EC2.**

---

## 📌 Project Overview

This project demonstrates a practical **DevOps CI/CD pipeline** for a Java application.

The pipeline automates the following workflow:

```text
Developer
    │
    │ git push
    ▼
┌───────────────┐
│    GitHub     │
│ Source Code   │
└───────┬───────┘
        │
        │ Webhook / Trigger
        ▼
┌───────────────┐
│    Jenkins    │
│    CI/CD      │
└───────┬───────┘
        │
        ├── Maven Build
        │
        ├── JUnit Tests
        │
        ├── Docker Build
        │
        ├── Docker Test
        │
        └── Push Image
                │
                ▼
        ┌───────────────┐
        │   Docker Hub  │
        │ Image Registry│
        └───────┬───────┘
                │
                │ Pull Image
                ▼
        ┌─────────────────────┐
        │ AWS EC2 Kubernetes  │
        │       Cluster       │
        └──────────┬──────────┘
                   │
                   ▼
             Kubernetes
             Deployment
                   │
                   ▼
              Java Pods
```

---

# 🎯 Project Objectives

The main objective is to build and demonstrate a complete CI/CD workflow using commonly used DevOps technologies.

### This project demonstrates:

* ✅ Git-based source code management
* ✅ Java application build using Maven
* ✅ Automated JUnit testing
* ✅ Jenkins Pipeline automation
* ✅ Docker image creation
* ✅ Docker container testing
* ✅ Docker Hub image publishing
* ✅ Kubernetes deployment
* ✅ Kubernetes rolling updates
* ✅ AWS EC2 infrastructure
* ✅ CI/CD automation from GitHub to Kubernetes
* ✅ Versioned Docker images using Jenkins Build Numbers

---

# 🏗️ Architecture

```text
                         ┌──────────────────┐
                         │     Developer    │
                         └────────┬─────────┘
                                  │
                                  │ git push
                                  ▼
                         ┌──────────────────┐
                         │     GitHub       │
                         │  Source Control  │
                         └────────┬─────────┘
                                  │
                                  │ Webhook
                                  ▼
                    ┌──────────────────────────┐
                    │         Jenkins          │
                    │                          │
                    │  ┌────────────────────┐  │
                    │  │ Maven Build        │  │
                    │  ├────────────────────┤  │
                    │  │ JUnit Test         │  │
                    │  ├────────────────────┤  │
                    │  │ Docker Build       │  │
                    │  ├────────────────────┤  │
                    │  │ Docker Test        │  │
                    │  ├────────────────────┤  │
                    │  │ Docker Push        │  │
                    │  └────────────────────┘  │
                    └────────────┬─────────────┘
                                 │
                                 │ Push
                                 ▼
                       ┌───────────────────┐
                       │    Docker Hub     │
                       │                   │
                       │ Versioned Images  │
                       │ :15 :16 :17 ...  │
                       └─────────┬─────────┘
                                 │
                                 │ Pull
                                 ▼
                  ┌──────────────────────────────┐
                  │        AWS EC2               │
                  │                              │
                  │     Kubernetes Cluster       │
                  │                              │
                  │   ┌──────────────────────┐   │
                  │   │ Kubernetes Deployment│   │
                  │   └──────────┬───────────┘   │
                  │              │               │
                  │       ┌──────┴──────┐        │
                  │       ▼             ▼        │
                  │   Java Pod      Java Pod     │
                  │   Replica 1     Replica 2    │
                  └──────────────────────────────┘
```

---

# 🛠️ Technology Stack

| Technology     | Purpose                                  |
| -------------- | ---------------------------------------- |
| **Java 17+**   | Application development                  |
| **Maven**      | Build, dependency management and testing |
| **JUnit**      | Unit testing                             |
| **Git**        | Version control                          |
| **GitHub**     | Source code repository                   |
| **Jenkins**    | CI/CD automation                         |
| **Docker**     | Application containerization             |
| **Docker Hub** | Container image registry                 |
| **Kubernetes** | Container orchestration                  |
| **kubectl**    | Kubernetes CLI                           |
| **AWS EC2**    | Cloud infrastructure                     |
| **Linux**      | Server operating system                  |
| **Groovy**     | Jenkins Pipeline scripting               |

---

# 📂 Repository Structure

```text
java-jenkins-docker/
│
├── src/
│   ├── main/
│   │   └── java/
│   │       └── com/
│   │           └── example/
│   │               └── App.java
│   │
│   └── test/
│       └── java/
│           └── com/
│               └── example/
│                   └── AppTest.java
│
├── k8s/
│   └── deployment.yaml
│
├── pom.xml
├── Dockerfile
├── docker-compose.yml
├── Jenkinsfile
└── README.md
```

### Important Files

| File                  | Description                         |
| --------------------- | ----------------------------------- |
| `App.java`            | Main Java application               |
| `AppTest.java`        | JUnit unit test                     |
| `pom.xml`             | Maven project configuration         |
| `Dockerfile`          | Docker image definition             |
| `docker-compose.yml`  | Local container orchestration       |
| `Jenkinsfile`         | CI/CD Pipeline definition           |
| `k8s/deployment.yaml` | Kubernetes deployment configuration |
| `README.md`           | Project documentation               |

---

# 🔄 CI/CD Pipeline

The Jenkins pipeline follows these stages:

```text
Checkout
   │
   ▼
Maven Build
   │
   ▼
JUnit Test
   │
   ▼
Docker Build
   │
   ▼
Docker Test
   │
   ▼
Docker Hub Push
   │
   ▼
Kubernetes Deployment
   │
   ▼
Deployment Verification
```

---

# 1️⃣ Source Code Checkout

Jenkins retrieves the source code from GitHub.

```groovy
stage('Checkout') {
    steps {
        checkout scm
    }
}
```

---

# 2️⃣ Maven Build

The Java application is compiled and packaged using Maven.

```bash
mvn clean package
```

This performs:

```text
clean
  ↓
compile
  ↓
test
  ↓
package
  ↓
JAR
```

The generated JAR file is stored inside:

```text
target/
```

---

# 3️⃣ Automated Testing

JUnit tests are executed through Maven:

```bash
mvn test
```

The pipeline continues only when the tests pass.

```text
JUnit Test
     │
     ├── FAIL → Pipeline stops
     │
     └── PASS → Continue
```

---

# 4️⃣ Docker Image Build

After successful testing, Jenkins creates the Docker image:

```bash
docker build \
  -t YOUR_DOCKER_USERNAME/java-jenkins-docker:${BUILD_NUMBER} \
  .
```

The Jenkins build number is used as the image version.

For example:

```text
java-jenkins-docker:15
java-jenkins-docker:16
java-jenkins-docker:17
```

This provides traceability between:

```text
Jenkins Build
      ↓
Docker Image
      ↓
Kubernetes Deployment
```

---

# 5️⃣ Docker Container Test

Before publishing the image, Jenkins runs the container:

```bash
docker run --rm \
  YOUR_DOCKER_USERNAME/java-jenkins-docker:${BUILD_NUMBER}
```

Expected output:

```text
Hello from Java Application for Jenkins CI/CD!
```

This verifies that the generated Docker image can successfully start the application.

---

# 6️⃣ Push Image to Docker Hub

After successful testing, Jenkins authenticates with Docker Hub and pushes the image:

```bash
docker push \
  YOUR_DOCKER_USERNAME/java-jenkins-docker:${BUILD_NUMBER}
```

The image is then available to the Kubernetes cluster.

```text
Jenkins
   │
   │ docker push
   ▼
Docker Hub
   │
   │ docker pull
   ▼
Kubernetes
```

---

# 7️⃣ Kubernetes Deployment

The Kubernetes cluster runs on AWS EC2.

The deployment uses the Docker Hub image:

```yaml
apiVersion: apps/v1
kind: Deployment

metadata:
  name: java-jenkins-app

spec:
  replicas: 2

  selector:
    matchLabels:
      app: java-jenkins-app

  template:
    metadata:
      labels:
        app: java-jenkins-app

    spec:
      containers:
        - name: java-app
          image: YOUR_DOCKER_USERNAME/java-jenkins-docker:latest
          imagePullPolicy: Always
```

The application runs with two replicas:

```text
              Deployment
                   │
             ┌─────┴─────┐
             ▼           ▼
          Pod 1        Pod 2
          Java         Java
```

---

# 8️⃣ Kubernetes Deployment from Jenkins

Jenkins can update the running Kubernetes deployment using:

```bash
kubectl set image deployment/java-jenkins-app \
java-app=YOUR_DOCKER_USERNAME/java-jenkins-docker:${BUILD_NUMBER}
```

Then Jenkins waits for the rollout:

```bash
kubectl rollout status deployment/java-jenkins-app
```

This provides an automated deployment workflow.

---

# 🔐 Jenkins Credentials

Credentials are **not stored inside the Git repository**.

Jenkins Credentials are used for:

### Docker Hub

```text
Credential ID:
dockerhub-creds
```

### Kubernetes

```text
Credential ID:
kubeconfig
```

This keeps sensitive authentication information outside the source code.

> ⚠️ Never commit Docker Hub passwords, access tokens, AWS credentials, or Kubernetes admin credentials to GitHub.

---

# ⚙️ Prerequisites

Install the following components before running the project:

### Local Development

```text
Java 17+
Maven
Git
Docker
Docker Compose
```

### Jenkins Server

```text
Jenkins
Java
Maven
Git
Docker CLI
Docker daemon access
kubectl
```

### Kubernetes EC2

```text
Linux
containerd
kubeadm
kubelet
kubectl
CNI plugin
```

### Cloud

```text
AWS EC2
Docker Hub account
GitHub account
```

---

# 🚀 Local Setup

## Clone Repository

```bash
git clone <YOUR_REPOSITORY_URL>
```

Navigate into the project:

```bash
cd java-jenkins-docker
```

---

# ☕ Run Java Application

Build the project:

```bash
mvn clean package
```

Run:

```bash
java -jar target/java-jenkins-docker-1.0-SNAPSHOT.jar
```

Expected:

```text
Hello from Java Application for Jenkins CI/CD!
```

---

# 🧪 Run Tests

```bash
mvn test
```

Expected:

```text
BUILD SUCCESS
```

---

# 🐳 Build Docker Image

```bash
docker build \
  -t java-jenkins-docker:latest \
  .
```

Verify:

```bash
docker images
```

---

# ▶️ Run Docker Container

```bash
docker run --rm java-jenkins-docker:latest
```

Expected:

```text
Hello from Java Application for Jenkins CI/CD!
```

---

# 🐳 Docker Compose

Start the application:

```bash
docker compose up --build
```

Stop:

```bash
docker compose down
```

---

# ☸️ Kubernetes Deployment

Apply the Kubernetes deployment:

```bash
kubectl apply -f k8s/deployment.yaml
```

Check the deployment:

```bash
kubectl get deployments
```

Check Pods:

```bash
kubectl get pods
```

Check Pod details:

```bash
kubectl describe pod <POD_NAME>
```

Check application logs:

```bash
kubectl logs <POD_NAME>
```

Expected:

```text
Hello from Java Application for Jenkins CI/CD!
```

---

# 🔍 Kubernetes Verification

Check nodes:

```bash
kubectl get nodes
```

Check all resources:

```bash
kubectl get all
```

Check deployment rollout:

```bash
kubectl rollout status deployment/java-jenkins-app
```

Check deployed image:

```bash
kubectl get pod <POD_NAME> \
-o jsonpath='{.spec.containers[0].image}'
```

---

# 🔁 Rolling Update

When a new Jenkins build creates a new Docker image:

```text
Build 17
   ↓
java-jenkins-docker:17
```

Jenkins deploys:

```bash
kubectl set image deployment/java-jenkins-app \
java-app=YOUR_DOCKER_USERNAME/java-jenkins-docker:17
```

Kubernetes performs the rollout:

```text
Old Version
     │
     ▼
┌─────────────┐
│ Java Pod v16│
└─────────────┘
       │
       │ Rolling Update
       ▼
┌─────────────┐
│ Java Pod v17│
└─────────────┘
```

Check rollout history:

```bash
kubectl rollout history deployment/java-jenkins-app
```

---

# ↩️ Kubernetes Rollback

If a deployment needs to be reverted:

```bash
kubectl rollout undo deployment/java-jenkins-app
```

Check:

```bash
kubectl rollout status deployment/java-jenkins-app
```

This demonstrates a basic Kubernetes deployment recovery workflow.

---

# 📊 Jenkins Pipeline Example

The Jenkinsfile contains the following logical stages:

```text
┌─────────────────────┐
│      Checkout       │
└──────────┬──────────┘
           ▼
┌─────────────────────┐
│    Maven Build      │
└──────────┬──────────┘
           ▼
┌─────────────────────┐
│     JUnit Test      │
└──────────┬──────────┘
           ▼
┌─────────────────────┐
│    Docker Build     │
└──────────┬──────────┘
           ▼
┌─────────────────────┐
│     Docker Test     │
└──────────┬──────────┘
           ▼
┌─────────────────────┐
│   Docker Hub Push   │
└──────────┬──────────┘
           ▼
┌─────────────────────┐
│ Kubernetes Deploy   │
└──────────┬──────────┘
           ▼
┌─────────────────────┐
│ Deployment Verify   │
└─────────────────────┘
```

---

# 🔑 Key DevOps Concepts Demonstrated

### Continuous Integration

Every code change can trigger:

```text
Git Push
   ↓
Jenkins
   ↓
Build
   ↓
Test
```

### Continuous Delivery / Deployment

After successful CI:

```text
Docker Build
     ↓
Docker Hub
     ↓
Kubernetes
```

### Containerization

The Java application is packaged into a portable Docker image.

### Image Versioning

Jenkins Build Numbers are used as image versions:

```text
:15
:16
:17
:18
```

### Infrastructure

The application runs on AWS EC2 infrastructure.

### Container Orchestration

Kubernetes manages:

* Pods
* Deployments
* Replicas
* Rollouts
* Rollbacks

---

# 🧠 What I Learned

Through this project, I practiced:

* Java application packaging with Maven
* Maven dependency management
* JUnit automated testing
* Git and GitHub workflows
* Jenkins Declarative Pipeline
* Jenkins credentials management
* Docker image creation
* Docker container execution
* Docker image versioning
* Docker Hub image registry
* Kubernetes Deployments
* Kubernetes Pods and replicas
* Kubernetes rolling updates
* Kubernetes rollback
* `kubectl` troubleshooting
* AWS EC2 infrastructure
* End-to-end CI/CD automation

---

# 🧩 Troubleshooting Commands

## Jenkins

```bash
docker logs <jenkins-container>
```

## Docker

```bash
docker ps
docker images
docker logs <container>
docker inspect <container>
```

## Kubernetes

```bash
kubectl get nodes
kubectl get pods
kubectl get pods -o wide
kubectl describe pod <pod>
kubectl logs <pod>
kubectl get deployments
kubectl describe deployment <deployment>
kubectl rollout status deployment/<deployment>
kubectl rollout history deployment/<deployment>
```

---

# 📈 Future Improvements

This project can be extended further with:

* [ ] GitHub webhook-based Jenkins triggering
* [ ] Kubernetes Service / Ingress
* [ ] AWS EKS deployment
* [ ] Terraform infrastructure provisioning
* [ ] Helm chart packaging
* [ ] Argo CD GitOps deployment
* [ ] Prometheus monitoring
* [ ] Grafana dashboards
* [ ] SonarQube code quality analysis
* [ ] Trivy container vulnerability scanning
* [ ] Kubernetes Secrets
* [ ] ConfigMaps
* [ ] Horizontal Pod Autoscaler
* [ ] Blue-Green deployment
* [ ] Canary deployment
* [ ] Slack / email notifications

---

# 🎓 Project Outcome

The final implementation demonstrates a complete DevOps workflow:

```text
                 SOURCE
                   │
                   ▼
                GitHub
                   │
                   ▼
                Jenkins
                   │
          ┌────────┴────────┐
          ▼                 ▼
       Build              Test
          │                 │
          └────────┬────────┘
                   ▼
             Docker Build
                   │
                   ▼
             Docker Test
                   │
                   ▼
              Docker Hub
                   │
                   ▼
            Kubernetes
                   │
             ┌─────┴─────┐
             ▼           ▼
           Pod 1       Pod 2
             │           │
             └─────┬─────┘
                   ▼
             Java Application
```

---

# 👨‍💻 Author

**Aniket Chatur**

DevOps / Cloud / SRE / Infrastructure Engineering

### Areas of Interest

```text
DevOps
Cloud
Kubernetes
Docker
CI/CD
AWS
Azure
GCP
Terraform
Ansible
Helm
Argo CD
Prometheus
Grafana
Linux
```

---

# ⭐ Project Highlights

> **GitHub → Jenkins → Maven → JUnit → Docker → Docker Hub → Kubernetes → AWS EC2**

This project demonstrates how a developer's source-code change can be automatically transformed into a tested container image and deployed workload running on Kubernetes.

---

## 📌 Disclaimer

This project is created for **learning, hands-on DevOps practice, and portfolio demonstration**. Infrastructure configurations should be reviewed and hardened before being used in production.
