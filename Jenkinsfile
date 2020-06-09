pipeline {
  agent any
  stages {
    

    stage('Set New TestFlight App Version') {
      steps {
        echo 'Genrate TestFlight App Version'
        sh 'BUILD_NUMBER=$(($BUILD_NUMBER + 1)) $(/usr/libexec/PlistBuddy -c \"Set :CFBundleVersion 1.0.${BUILD_NUMBER}\" $WORKSPACE/Info.plist)'
      }
    }
  }
post {
    always {
        archiveArtifacts artifacts: '$WORKSPACE/**', fingerprint: true
    }
}

  
  tools {
    nodejs 'nodeLatest'
  }
}