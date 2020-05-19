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
    stage('Clean up') {
      steps {
        sh "echo 'stop background flask job'"
        sh "sudo kill %1 || true"
      }
    }
    stage('Deploy') {
      steps {
        sh "echo 'start flask as background job'"
        sh "sudo python3 server.py >> log.txt 2>&1 &"
      }
    }
  }
}