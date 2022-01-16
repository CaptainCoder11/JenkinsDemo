node{
   stage('SCM Checkout'){
       git credentialsId: 'mygithub', url: 'https://github.com/CaptainCoder11/JenkinsDemo.git'
   }
   stage('Mvn Package'){
     def mvnHome = tool name: 'maven-3', type: 'maven'
     def mvnCMD = "${mvnHome}/bin/mvn"
     sh "${mvnCMD} clean package"
   }
   stage('Build Docker Image'){
     sh 'docker build -t ruchit/my-app:2.0.0 .'
   }
  
   stage('Run Container on Dev Server'){
     def dockerRun = 'docker run -p 8080:8080 -d --name my-app ruchit/my-app:2.0.0'
   }
}
