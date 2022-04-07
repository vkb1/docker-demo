pipeline {
  environment {
    imagename = "bvinodkumar2008/docker-jenkins-proj"
    registryCreds = "docker-creds"
    dockerImage = ''
  }
  agent any
  stages {
    stage('Clone src') {
      steps {
        git([url: 'https://github.com/vkb1/docker-demo', branch: 'master'])
    }
    
    stage('Build image') {
      steps {
        dockerImage = docker.build imagename
      }
    }
  }
  
}
