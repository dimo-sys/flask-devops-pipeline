pipeline {
  agent any

  stages {
    stage('Build Docker Image') {
      steps {
        echo "Building Docker image..."
        sh 'docker build -t flask-app:latest .'
      }
    }

    stage('Deploy to K8s') {
      steps {
        echo "Deploying to Kubernetes..."
        sh 'kubectl apply -f deployment.yaml'
        sh 'kubectl apply -f service.yaml'
      }
    }
  }
}
