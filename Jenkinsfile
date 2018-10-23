pipeline {
  agent any
  stages {
    stage('Compile') {
      parallel {
        stage('Compile') {
          steps {
            sh 'mvn install'
            echo 'Done'
          }
        }
        stage('Hello') {
          steps {
            echo 'Hello'
          }
        }
      }
    }
    stage('Test') {
      parallel {
        stage('Test') {
          steps {
            sh 'mvn test'
          }
        }
        stage('SonarQube') {
          steps {
            withSonarQubeEnv('SonarQube') {
              sh 'mvn sonar:sonar'
            }

          }
        }
      }
    }
    stage('Static Code Analysis') {
      steps {
        waitForQualityGate true
      }
    }
  }
}