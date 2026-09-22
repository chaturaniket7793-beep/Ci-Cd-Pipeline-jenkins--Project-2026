pipeline {

    agent any

    tools {
        jdk 'JDK17'
        maven 'maven-3.9'
    }

    environment {
        DOCKER_IMAGE = "aniketchatur/java-pipeline-repo:latest"
    }

    stages {

        stage('Maven Build') {
            steps {
                sh 'mvn clean package -DskipTests'
            }
        }

        stage('Maven Test') {
            steps {
                sh 'mvn test'
            }
        }

        stage('Docker Build') {
            steps {
                sh 'docker build -t $DOCKER_IMAGE .'
            }
        }

        stage('Docker Push') {
            steps {
                withCredentials([
                    usernamePassword(
                        credentialsId: 'java-pipeline-123',
                        usernameVariable: 'DOCKER_USERNAME',
                        passwordVariable: 'DOCKER_PASSWORD'
                    )
                ]) {
                    sh '''
                        echo "$DOCKER_PASSWORD" | docker login -u "$DOCKER_USERNAME" --password-stdin
                        docker push "$DOCKER_IMAGE"
                        docker logout
                    '''
                }
            }
        }

        stage('Kubernetes Deploy') {
            steps {
                withCredentials([
                    file(
                        credentialsId: 'kubeconfig-ec2',
                        variable: 'KUBECONFIG_FILE'
                    )
                ]) {
                    sh '''
                        export KUBECONFIG="$KUBECONFIG_FILE"

                        echo "Checking Kubernetes connection..."
                        kubectl get nodes

                        echo "Deploying application..."
                        kubectl apply -f k8s/deployment.yaml
                    '''
                }
            }
        }

        stage('Kubernetes Verify') {
            steps {
                withCredentials([
                    file(
                        credentialsId: 'kubeconfig-ec2',
                        variable: 'KUBECONFIG_FILE'
                    )
                ]) {
                    sh '''
                        export KUBECONFIG="$KUBECONFIG_FILE"

                        echo "Kubernetes Nodes:"
                        kubectl get nodes

                        echo "Application Pods:"
                        kubectl get pods

                        echo "Application Service:"
                        kubectl get svc
                    '''
                }
            }
        }
    }

    post {
        success {
            echo 'CI/CD Pipeline completed successfully!'
        }

        failure {
            echo 'CI/CD Pipeline failed!'
        }
    }
}