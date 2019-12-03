#!groovy

pipeline {
  agent none
  
  options{
    buildDiscarder(logRotator(numToKeepStr :'5', artifactNumToKeepStr: '5'))
  }
  
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
    stage('Build Artifact') {
      agent any
      steps {
        sh 'echo hello from Build Artifact'
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
