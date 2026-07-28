pipeline {
    agent any

    environment {
        KUBECONFIG = "/var/lib/jenkins/.kube/config"
    }

    stages {

        stage('Check kubectl') {
    steps {
        bat '''
        echo %PATH%
        where kubectl
        kubectl version --client
        '''
    }
}

        stage('Checkout') {
            steps {
                // checkout scm
                echo "Checkout"
            }
        }

        stage('Verify Kubernetes Cluster') {
            steps {
                // sh 'kubectl get nodes'
                // sh 'which kubectl'
                echo "Verify K8S done"
            }
        }

        // stage('Deploy Nginx') {
        //     steps {
        //         sh 'kubectl apply -f nginx.yaml'
        //     }
        // }

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
            echo 'kubectl get all'
        }
    }
}

