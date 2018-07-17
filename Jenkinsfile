pipeline {
  agent any
  stages {
    stage('github prep') {
      steps {
        git 'https://github.com/jglick/simple-maven-project-with-tests.git'
      }
    }
    stage('bld') {
      steps {
        sh 'mvn -Dmaven.test.failure.ignore clean package'
      }
    }
    stage('results') {
      parallel {
        stage('results') {
          steps {
            junit '**/target/surefire-reports/TEST-*.xml'
          }
        }
        stage('archive') {
          steps {
            archiveArtifacts(artifacts: 'target/*.jar', allowEmptyArchive: true)
          }
        }
      }
    }
  }
}