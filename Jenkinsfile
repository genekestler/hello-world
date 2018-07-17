pipeline {
  agent any
  stages {
    stage('GitHub Prep') {
      steps {
        git 'https://github.com/jglick/simple-maven-project-with-tests.git'
      }
    }
    stage('Maven Build') {
      steps {
        sh 'mvn -Dmaven.test.failure.ignore clean package'
      }
    }
    stage('Junit results') {
      parallel {
        stage('Junit results') {
          steps {
            junit(testResults: '**/target/surefire-reports/TEST-*.xml', allowEmptyResults: true)
          }
        }
        stage('') {
          steps {
            archiveArtifacts(artifacts: 'target/*.jar', allowEmptyArchive: true)
          }
        }
      }
    }
  }
}