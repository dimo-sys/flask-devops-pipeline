pipeline {
    agent any

    stages {
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t flask-app:latest .'
            }
        }

        stage('Deploy to K8s') {
            steps {
                sh 'kubectl apply -f deployment.yaml'
            }
        }
    }
}
