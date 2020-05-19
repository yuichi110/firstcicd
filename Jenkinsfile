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
  }
}