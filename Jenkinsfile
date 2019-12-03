#!groovy

pipeline {
  agent none
  stages {
    stage('Maven Install') {
      agent {
        docker {
          image 'maven:3.3.3'
        }
      }
      steps {
        sh 'mvn clean package'
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
        sh 'docker run -d 9090:8080 sandeepbhardwaj/spring-boot-jenkins:latest'
      }
    }
  }
}
