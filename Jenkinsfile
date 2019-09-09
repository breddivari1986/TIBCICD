pipeline {
  agent any
  stages {
    stage('BuildEar') {
      parallel {
        stage('BuildEar') {
          steps {
            build 'BuildEar'
          }
        }
        stage('SlackNotify-Package') {
          steps {
            slackSend()
          }
        }
        stage('') {
          steps {
            catchError(buildResult: 'BuildEar Failed', message: 'BuildEar Failed', stageResult: 'failed')
          }
        }
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
      parallel {
        stage('Deploy2Admin') {
          steps {
            build 'Deploy'
          }
        }
        stage('SlackNotify-Deployment') {
          steps {
            slackSend()
          }
        }
      }
    }
    stage('UnitTests') {
      parallel {
        stage('UnitTests') {
          steps {
            sleep 9000
          }
        }
        stage('SlackNotify-TestResults') {
          steps {
            slackSend()
          }
        }
      }
    }
  }
}