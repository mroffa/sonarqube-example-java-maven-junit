pipeline {
  agent any
  stages {
    stage('Test') {
      agent {
        docker 'maven:3-alpine'
      }
      steps {
        sh 'mvn test'
      }
    }
    stage('Example Test') {
      agent {
        docker 'openjdk:8-jre'
      }
      steps {
        echo 'Hello, JDK'
        sh 'java -version'
      }
    }
  }
}