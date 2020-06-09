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
            sh 'mkdir archive'
            sh 'echo MyIntuitiveApp_QA > build/MyIntuitive.app'
            sh 'zip zipFile: ''MyIntuitiveApp_QA.zip'', archive: false, dir: ''build'''
            
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