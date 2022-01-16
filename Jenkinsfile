pipeline{
    agent any
    environment{
        NEW_VERSION = '1.3.0'
    }

    stages{
       stage('Checkout') {
      steps {
        script {
           checkout([$class: 'GitSCM', branches: [[name: "*/$GIT_BRANCH"]], doGenerateSubmoduleConfigurations: false, extensions: [], gitTool: 'Default', submoduleCfg: [], userRemoteConfigs: [[credentialsId: "$GIT_CREDS_ID", url: "$GIT_URL"]]])
           sh "ls -lart ./*"
          }
       }
    }
    }
}
