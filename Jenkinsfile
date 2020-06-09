pipeline {
  agent any
  stages {
    stage('Set New TestFlight App Version') {
      steps {
        echo 'Genrate TestFlight App Version'
        sh 'BUILD_NUMBER=$(($BUILD_NUMBER + 1)) $(/usr/libexec/PlistBuddy -c "Set :CFBundleVersion 1.0.${BUILD_NUMBER}" $WORKSPACE/Info.plist)'
      }
    }

    stage('') {
      steps {
        sshagent() {
          sshagent()
        }

      }
    }

  }
  tools {
    nodejs 'nodeLatest'
  }
  post {
    always {
      archiveArtifacts(artifacts: 'build/', fingerprint: true)
    }

  }
}