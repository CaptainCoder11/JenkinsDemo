node{
   stage('SCM Checkout'){
      checkout([$class: 'GitSCM',
        branches: [[name: '*/main']],
        extensions: [[$class: 'CloneOption', timeout: 120]],
        gitTool: 'Default', 
        userRemoteConfigs: [[url: 'https://github.com/CaptainCoder11/JenkinsDemo.git']]
    ])
   }
   stage('Build Docker Image'){
     sh 'docker build -t ruchit/my-app:2.0.0 .'
   }
  
   stage('Run Container on Dev Server'){
     def dockerRun = 'docker run -p 8080:8080 -d --name my-app ruchit/my-app:2.0.0'
   }
}
