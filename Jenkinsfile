pipeline {
  agent any
  environment {
    TIMESTAMP = sh(script: "date +%Y%m%d-%H%M%S", returnStdout: true).trim()
  }
  stages {
    stage('Pre Check') {
      steps {
        sh "echo ${TIMESTAMP}"
        sh "python3 --version"
      }
    }
    stage('Clean') {
      steps {
        sh "kill %1 || true"
      }
    }
    stage('Deploy') {
      steps {
        sh "python3 server.py >> log.txt 2>&1 &"
      }
    }
  }
}