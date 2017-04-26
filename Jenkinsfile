pipeline {
  agent any
  stages {
    stage('Initialize') {
      steps {
        echo 'firsts step of the pipe'
      }
    }
    stage('testing') {
      steps {
        sleep 10
      }
    }
    stage('deploy') {
      steps {
        fileExists 'readme'
      }
    }
  }
}