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
    stage('Docker Run') {
      agent any
      steps {
        sh 'docker run -d -p  9090:8080 sandeepbhardwaj/spring-boot-jenkins:latest'
      }
    }
  }
}
