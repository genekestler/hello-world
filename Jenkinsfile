pipeline {
  agent any
  stages {
    stage('Initialize') {
      steps {
        echo 'first step of the pipe'
      }
    }
    stage('Testing') {
      steps {
        sleep 6
      }
    }
    stage('Deploy') {
      steps {
        sh 'date'
      }
    }
  }
}