pipeline {
  agent any
  environment {
        JENKINS_PWD = credentials('JENKINS_PWD')
    }
  stages {
    stage('Set New TestFlight App Version') {
      steps {
        echo 'Genrate TestFlight App Version'
        sh 'BUILD_NUMBER=$(($BUILD_NUMBER + 1)) $(/usr/libexec/PlistBuddy -c "Set :CFBundleVersion 1.0.${BUILD_NUMBER}" $WORKSPACE/Info.plist)'

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
            sh 'zip -r -D $WORKSPACE/build/MyIntuitiveApp_QA.zip $WORKSPACE/ios/DerivedData/MyIntuitive/Build/Products/Release-iphonesimulator/MyIntuitive.app'
        }
    }

    stage('Upload-QA-SimulatorBuild') {
      steps {
        echo 'UPLOAD Simulator App'
        sh 'aws s3 cp $WORKSPACE/build/MyIntuitiveApp_QA.zip s3://dev-myintuitiveapps-1/qa/qa_app/MyIntuitiveApp_QA.zip'
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