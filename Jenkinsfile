pipeline {
  agent any
  stages {
    stage('get src') {
      steps {
        git 'https://github.com/jglick/simple-maven-project-with-tests.git'
      }
    }
    stage('mvn build') {
      steps {
        sh 'mvn -Dmaven.test.failure.ignore clean package'
      }
    }
    stage('result archive') {
      steps {
        junit(testResults: '**/target/surefire-reports/TEST-*.xml', allowEmptyResults: true)
        archiveArtifacts(artifacts: 'target/*.jar', allowEmptyArchive: true)
      }
    }
  }
}