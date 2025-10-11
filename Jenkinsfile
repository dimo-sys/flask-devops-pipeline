pipeline {
  agent any
  stages {
    stage('Clone') {
      steps {
        git 'https://github.com/dimo-sys/flask-devops-pipeline.git'
      }
    }
    stage('Build Docker Image') {
      steps {
        sh 'docker build -t flask-app:latest .'
      }
    }
    stage('Deploy to K8s') {
      steps {
        sh 'kubectl apply -f deployment.yaml'
        sh 'kubectl apply -f service.yaml'
      }
    }
  }
}
