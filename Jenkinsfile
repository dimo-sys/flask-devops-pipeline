pipeline {
    agent any

    environment {
        IMAGE_NAME = "flask-app"
        IMAGE_TAG = "latest"
    }

    stages {

        stage('Build Docker Image') {
            steps {
                echo "Building Docker image..."
                sh 'docker build -t ${IMAGE_NAME}:${IMAGE_TAG} .'
            }
        }

        stage('Push Docker Image (optional)') {
            when {
                expression { return false } // Disable for now, enable later if you use DockerHub
            }
            steps {
                echo "Skipping Docker push..."
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                echo "Deploying to Kubernetes..."
                sh 'kubectl apply -f deployment.yaml || true'
            }
        }
    }

    post {
        always {
            echo "Pipeline finished."
        }
    }
}
