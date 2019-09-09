pipeline {
  agent any
  stages {
    stage('SCM-Checkout') {
      steps {
        git(url: 'https://github.com/breddivari1986/TIBCICD', branch: 'master', poll: true)
      }
    }
    stage('ExportXml') {
      steps {
        build 'ExportXml'
      }
    }
    stage('UpdateGV') {
      steps {
        build 'UpdateGvXml'
      }
    }
    stage('Deploy2Admin') {
      steps {
        build 'Deploy'
      }
    }
    stage('UnitTests') {
      steps {
        sleep 9000
      }
    }
  }
}