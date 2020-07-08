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
            slackSend(color: '#D4DAD', message: "Job: ${env.JOB_NAME} with buildnumber ${env.BUILD_NUMBER} is started")
          }
        }

      }
    }   
  }
  post {
    success {
            slackSend(color: 'good', message: currentBuild.currentResult.rawBuild.getCause(Cause.UserIdCause).getUserId())
       }
       
       failure {
            slackSend(color: '#FF9FA1', message: currentBuild.currentResult)
       }
        
    }
  tools {
    nodejs 'nodeLatest'
  }
}