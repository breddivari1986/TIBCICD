pipeline {
  agent any
  stages {
    stage('SCM-Checkout') {
      steps {
        git(url: 'https://github.com/breddivari1986/TIBCICD.git', branch: 'master', poll: true, changelog: true, credentialsId: 'bbc3efab585838eb70e02fcacd46c68544ea2241')
      }
    }

    stage('ValidateProject') {
      steps {
        sleep 5
        build(job: 'Test', quietPeriod: 100)
      }
    }

    stage('BuildEar') {
      parallel {
        stage('BuildEar') {
          steps {
            sleep 2
          }
        }

        stage('SlackNotify-Buildear') {
          steps {
            sleep 5
          }
        }

        stage('UploadToNexus') {
          steps {
            sleep 5
          }
        }

      }
    }

    stage('ExportXml') {
      steps {
        sleep 2
      }
    }

    stage('UpdateGvXml') {
      steps {
        sleep 2
      }
    }

    stage('Deploy') {
      parallel {
        stage('Deploy') {
          steps {
            sleep 2
          }
        }

        stage('UnitTests') {
          steps {
            sleep(time: 9000, unit: 'MILLISECONDS')
          }
        }

      }
    }

    stage('SlackNotify-FinalStatus') {
      steps {
        slackSend()
      }
    }

    stage('Email') {
      steps {
        emailext(subject: 'Test', body: 'test1')
      }
    }

  }
}
