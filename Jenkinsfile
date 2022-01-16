node{
   stage('Initialize')
    {
        def dockerHome = tool 'mydocker'
        def mavenHome  = tool 'mymaven'
        env.PATH = "${dockerHome}/bin:${mavenHome}/bin:${env.PATH}"
    }
   stage('SCM Checkout'){
      checkout([$class: 'GitSCM',
        branches: [[name: '*/main']],
        extensions: [[$class: 'CloneOption', timeout: 120]],
        gitTool: 'Default', 
        userRemoteConfigs: [[url: 'https://github.com/CaptainCoder11/JenkinsDemo.git']]
    ])
   }
   stage('Build Docker Image'){
     label 'docker'
     sh 'docker build -t ruchit/my-app:2.0.0 .'
   }
  
   stage('Run Container on Dev Server'){
     label 'docker'
     def dockerRun = 'docker run -p 8080:8080 -d --name my-app ruchit/my-app:2.0.0'
   }
}
