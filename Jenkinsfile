pipeline {
  agent any
  environment {
    DOCKERHUB_CREDENTIALS = credentials('docker-hub-pat')
    APP_NAME = "prabhat3107/kuard-amd64"
    IMAGE_TAG = "newblue"
  }

  stages {
    stage('Build') {
      steps {
        sh 'docker build -t $APP_NAME:$IMAGE_TAG .'
      }
    }
    stage('docker hub login') {
      steps {
        sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
      }
    }
    stage('push image') {
      steps {
        sh 'docker push $APP_NAME:$IMAGE_TAG'
      }
    }
    stage('clean image') {
      steps {
        sh 'docker rmi $APP_NAME:$IMAGE_TAG'
      }
    }
  }
}