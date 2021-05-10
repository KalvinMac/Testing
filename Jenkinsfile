pipeline {
  agent any
  stages {
    stage('Set New TestFlight App Version') {
      when {
        expression {
          params.REQUESTED_ACTION_PLATFORM == 'iOS'
        }
      }
      steps {
        echo 'iOS'
      }
      when {
        expression {
          params.REQUESTED_ACTION_PLATFORM == 'Android'
        }
      }
      steps {
        echo 'Anroid'
      }
    }   
  }
  tools {
    nodejs 'nodeLatest'
  }
  parameters {
    choice(choices: ['iOS' , 'Anroid'], description: 'Which platform you want to build?', name: 'REQUESTED_ACTION_PLATFORM')
  }
}