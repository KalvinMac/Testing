pipeline {
  agent any
  stages {
    stage('Set New TestFlight App Version') {
      parallel {
        stage('Set New TestFlight App Version') {
          steps {
            echo 'Genrate TestFlight App Version'
            sh 'BUILD_NUMBER=$(($BUILD_NUMBER + 1)) $(/usr/libexec/PlistBuddy -c "Set :CFBundleVersion 1.0.${BUILD_NUMBER}" $WORKSPACE/Info.plist)'
          }
        }

        stage('slack') {
          steps {
            slackSend(message: 'Test Message', color: 'green', iconEmoji: 'thumbsup')
          }
        }

      }
    }

    stage('SecuirtyKey') {
      steps {
        echo 'Opening Keychain'
        sh 'security set-key-partition-list -S apple-tool:,apple:,codesign: -s -k ${JENKINS_PWD} ~/Library/Keychains/login.keychain-db'
      }
    }

    stage('zip file') {
      steps {
        sh 'zip -r $WORKSPACE/build/MyIntuitiveApp_QA.zip $WORKSPACE/ios/DerivedData/MyIntuitive/Build/Products/Release-iphonesimulator/MyIntuitive.app'
      }
    }

  }
  tools {
    nodejs 'nodeLatest'
  }
  environment {
    JENKINS_PWD = credentials('JENKINS_PWD')
  }
  post {
    always {
      archiveArtifacts(artifacts: 'build/*.zip,build/*.plist,build/*.ipa', fingerprint: true)
    }

  }
}