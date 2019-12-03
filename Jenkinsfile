#!groovy

pipeline {
  agent none
  
  options{
    buildDiscarder(logRotator(numToKeepStr :'5', artifactNumToKeepStr: '5'))
  }
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
  stages {
    stage('Build Artifact') {
      agent any
      steps {
        //sh './mvnw clean package'
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
