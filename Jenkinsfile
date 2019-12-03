#!groovy

pipeline {
  agent none
  stages {
    stage('Build Artifact') {
      agent any
      steps {
        sh './mvnw clean package'
      }
    }
    stage('Docker Build') {
      agent any
      steps {
        sh 'docker build -t sandeepbhardwaj/spring-boot-jenkins:latest .'
      }
    }
    
  }
}
