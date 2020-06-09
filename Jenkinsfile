pipeline {
  agent any
  stages {
    

    stage('Set New TestFlight App Version') {
      steps {
        echo 'Genrate TestFlight App Version'
        sh 'new=$(($BUILD_NUMBER + 1))'
        sh 'v=$(/usr/libexec/PlistBuddy -c \"Set :CFBundleVersion 1.0.${new}\" $WORKSPACE/ios/MyIntuitive/Info.plist)'
      }
    }

    

  }
  tools {
    nodejs 'nodeLatest'
  }
}