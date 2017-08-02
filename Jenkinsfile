pipeline {
  agent any
  stages {
    stage('build') {
      steps {
        parallel(
          "build": {
            echo 'we are building now'
            sleep 3
            
          },
          "verify file": {
            fileExists 'readme'
            
          }
        )
      }
    }
    stage('test') {
      steps {
        parallel(
          "test": {
            echo 'we are testing now'
            sh 'ping -c 3 localhost'
            
          },
          "sonarqube": {
            echo 'running sonarqube tests'
            
          },
          "selenium": {
            echo 'running selenium tests'
            
          }
        )
      }
    }
    stage('deploy') {
      steps {
        echo 'we are deploying now'
        sh 'dat'
      }
    }
  }
}