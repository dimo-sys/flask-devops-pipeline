pipeline {
    agent any

    environment {
        DOCKER_IMAGE = 'flask-app:latest'
    }

    stages {
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t ${DOCKER_IMAGE} .'
            }
        }

        stage('Deploy to K8s') {
            steps {
                sh '''
                if ! command -v kubectl &> /dev/null; then
                    echo "kubectl not found, skipping deploy stage";
                    exit 0;
                fi
                kubectl apply -f deployment.yaml
                '''
            }
        }
    }
}
