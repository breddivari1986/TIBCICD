pipeline {
  agent any
  stages {
    stage('BuildEar') {
      steps {
        build 'BuildEar'
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
  }
}