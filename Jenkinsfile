pipeline {
  agent any
  stages {
    

    stage('Set New TestFlight App Version') {
      steps {
        echo 'Genrate TestFlight App Version'
        script {
            NEW_BUILD_NUMBER=$(($BUILD_NUMBER + 1))
        }
        sh 'v=$(/usr/libexec/PlistBuddy -c \"Set :CFBundleVersion 1.0.${NEW_BUILD_NUMBER}\" $WORKSPACE/ios/MyIntuitive/Info.plist)'
      }
    }

    

  }
  tools {
    nodejs 'nodeLatest'
  }
}