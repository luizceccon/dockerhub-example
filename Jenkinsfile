pipeline {
  
  agent any
  
  environment {
    DOCKERHUB_CREDENTIALS = credentials('dockerhub-cred-luizceccon')
  }
  stages {
    stage('Build') {
      steps {
        sh 'docker build -t luizceccon/dp-alpine:latest .'
      }
    }
    stage('Login') {
      steps {
        sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
      }
    }
    stage('Push') {
      steps {
        sh 'docker push luizceccon/dp-alpine:latest'
      }
    }
  }
  post {
    always {
      sh 'docker logout'
    }
  }
}
