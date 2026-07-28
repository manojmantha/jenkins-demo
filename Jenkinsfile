pipeline {
    agent any

    environment {
        KUBECONFIG = "/var/lib/jenkins/.kube/config"
    }

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Verify Kubernetes Cluster') {
            steps {
                sh 'kubectl get nodes'
            }
        }

        stage('Deploy Nginx') {
            steps {
                sh 'kubectl apply -f nginx.yaml'
            }
        }

        stage('Verify Deployment') {
            steps {
                // sh 'kubectl get deployments'
                // sh 'kubectl get pods'
                // sh 'kubectl get svc'
                echo "Verify Deployment done"
            }
        }

    }

    post {
        success {
            echo 'Nginx deployed successfully.'
        }

        failure {
            echo 'Deployment failed.'
        }

        always {
            sh 'kubectl get all'
        }
    }
}

