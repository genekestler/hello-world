pipeline {
  agent any
  stages {
    stage('Get SRC') {
      steps {
        git 'https://github.com/jglick/simple-maven-project-with-tests.git'
      }
    }
    stage('MVN Build') {
      steps {
        sh 'mvn -Dmaven.test.failure.ignore clean package'
      }
    }
    stage('JUnit Results') {
      steps {
        junit(testResults: '**/target/surefire-reports/TEST-*.xml', allowEmptyResults: true)
        archiveArtifacts(artifacts: 'target/*.jar', allowEmptyArchive: true)
      }
    }
  }
}