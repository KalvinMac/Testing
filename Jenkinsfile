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
            slackSend(color: 'good', message: "Job: ${env.JOB_NAME} with buildnumber ${env.BUILD_NUMBER} is started")
          }
        }

      }
    }
    post {
        always {
	   
            slackSend(currentBuild.currentResult)
            
        }
    }

  }
  tools {
    nodejs 'nodeLatest'
  }
}