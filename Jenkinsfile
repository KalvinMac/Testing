pipeline {
  agent any
  stages {
    stage('Set New TestFlight App Version') {
      parallel {
        stage('Set New TestFlight App Version') {
          steps {
            echo 'Genrate TestFlight App Version'
          }
        }

        stage('Notify') {
          steps {
            slackSend(color: 'red')
          }
        }

      }
    }

  }
  tools {
    nodejs 'nodeLatest'
  }
}