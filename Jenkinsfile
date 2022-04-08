pipeline {
  environment {
    imagename = "bvinodkumar2008/docker-jenkins-proj"
    registryCredential = 'docker-creds'
    dockerImage = ''
  }
  agent any
  stages {
    stage('Cloning Git') {
      steps {
        sh 'ls -al'
        sh 'pwd'
        git([url: 'https://github.com/vkb1/docker-demo.git', branch: 'master'])
        sh 'pwd'
      }
    }
    stage('Building image') {
      steps{
        sh 'pwd'
        script {
          dockerImage = docker.build imagename
        }
        sh 'pwd'
      }
    }
    stage('Deploy Image') {
      steps{
        script {
          docker.withRegistry( '', registryCredential ) {
            dockerImage.push("$BUILD_NUMBER")
             dockerImage.push('latest')

          }
        }
      }
    }
    stage('Remove Unused docker image') {
      steps{
        sh "docker rmi $imagename:$BUILD_NUMBER"
         sh "docker rmi $imagename:latest"

      }
    }
  }
}
