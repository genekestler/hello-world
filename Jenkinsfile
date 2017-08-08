pipeline {
  agent any
  stages {
    stage('pull gith') {
      steps {
        git 'https://github.com/jglick/simple-maven-project-with-tests.git'
      }
    }
    stage('build') {
      steps {
        sh 'mvn clean package'
      }
    }
    stage('junit results') {
      steps {
        parallel(
          "junit results": {
            junit(testResults: '**/target/surefire-reports/TEST-*.xml', allowEmptyResults: true)
            
          },
          "archive": {
            archiveArtifacts(artifacts: 'target/*.jar', allowEmptyArchive: true)
            
          }
        )
      }
    }
  }
}