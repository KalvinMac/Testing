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
            wrap(delegate: [$class: 'BuildUser']) {
              slackSend(color: '#D4DAD', message: "Job: ${env.JOB_NAME} with buildnumber ${env.BUILD_NUMBER} is started by ${env.BUILD_USER}", iconEmoji: 'thumbsup:')
            }

          }
        }

      }
    }

  }
  tools {
    nodejs 'nodeLatest'
  }
  post {
    success {
      slackSend(color: 'good', message: currentBuild.currentResult)
    }

    failure {
      slackSend(color: '#FF9FA1', message: currentBuild.currentResult)
    }

  }
}