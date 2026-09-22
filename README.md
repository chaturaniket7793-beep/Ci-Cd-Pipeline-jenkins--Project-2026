# 🚀 Java CI/CD Pipeline with Jenkins, Docker & Kubernetes

A hands-on DevOps project demonstrating an end-to-end CI/CD pipeline for a Java application using **Jenkins, Maven, Docker, Docker Hub, Kubernetes, and AWS EC2**.

## 🏗️ Architecture

```text
Developer
    │
    ▼
 GitHub
    │
    ▼
 Jenkins
    │
    ├── Maven Build
    ├── JUnit Test
    ├── Docker Build
    └── Docker Push
           │
           ▼
      Docker Hub
           │
           ▼
   AWS EC2 Kubernetes
           │
           ▼
      Java Pods
```

## 🛠️ Technologies

* Java 17+
* Maven
* Git & GitHub
* Jenkins
* Docker
* Docker Hub
* Kubernetes
* AWS EC2
* Linux

## 📂 Project Structure

```text
java-jenkins-docker/
│
├── src/
│   ├── main/java/com/example/App.java
│   └── test/java/com/example/AppTest.java
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

## 🔄 CI/CD Pipeline

```text
GitHub
   ↓
Jenkins
   ↓
Maven Build
   ↓
JUnit Test
   ↓
Docker Build
   ↓
Docker Test
   ↓
Docker Hub
   ↓
Kubernetes Deployment
```

## ▶️ Run Locally

### Build & Test

```bash
mvn clean package
mvn test
```

### Run Java Application

```bash
java -jar target/java-jenkins-docker-1.0-SNAPSHOT.jar
```

### Build Docker Image

```bash
docker build -t java-jenkins-docker:latest .
```

### Run Container

```bash
docker run --rm java-jenkins-docker:latest
```

## ☸️ Kubernetes Deployment

```bash
kubectl apply -f k8s/deployment.yaml
```

Check deployment:

```bash
kubectl get deployments
kubectl get pods
```

View application logs:

```bash
kubectl logs <pod-name>
```

## 🎯 Key Learning

This project demonstrates:

* CI/CD automation with Jenkins
* Maven build and JUnit testing
* Docker containerization
* Docker Hub image publishing
* Kubernetes deployment
* AWS EC2 infrastructure
* Kubernetes rolling updates

## 👨‍💻 Author

**Aniket Chatur**

DevOps | Cloud | Kubernetes | Docker | CI/CD | AWS
