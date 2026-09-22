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