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

        stage('slack') {
          steps {
            notifySlack()
          }
        }

      }
    }

  }
  tools {
    nodejs 'nodeLatest'
  }
}