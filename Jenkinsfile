pipeline {
  agent any
  stages {
    stage('Install') {
      steps {
        sh 'npm install'
      }
    }
    stage('Build') {
      steps {
        sh 'npm run build'
      }
    }
    stage('Test') {
      steps {
        sh 'npm run test'
        emailext(subject: 'Approve Test', body: 'Please approve this tests to continue with the deployment', attachLog: true, to: 'tester')
        input(message: 'Approve?', submitter: 'tester', ok: 'Please Accept')
      }
    }
  }
}