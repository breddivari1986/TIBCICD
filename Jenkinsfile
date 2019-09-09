pipeline {
  agent any
  stages {
    stage('SCM-Checkout') {
      steps {
        git(url: 'https://github.com/breddivari1986/TIBCICD', branch: 'master', poll: true)
      }
    }
    stage('ValidateProject') {
      parallel {
        stage('ValidateProject') {
          steps {
            build 'ExportXml'
          }
        }
        stage('SlackNotify-ProjectReport') {
          steps {
            slackSend()
          }
        }
      }
    }
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
    stage('UpdateGvXml') {
      steps {
        build 'UpdateGvXml'
      }
    }
    stage('Deploy') {
      parallel {
        stage('Deploy') {
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
    stage('SlackNotify-FinalStatus') {
      steps {
        slackSend()
      }
    }
  }
}