#!groovy

node('master'){
 
 properties([
    buildDiscarder(logRotator(numToKeepStr: '3')),
    pipelineTriggers([
        pollSCM('* * * * *')
    ])
])

 def mavenHome = tool name: 'maven3.6.0', type: 'maven'
 
 stage('CheckoutCode') {
 git branch: 'master', credentialsId: '7467f260-7644-4317-b58f-1439a397ceec', url: 'https://github.com/devops122/Maven-Web-Project.git'
 }  
  
  stage('Build') {
 
    sh "${mavenHome}/bin/mvn clean package"
  }

  stage('ExecuteSonarQubeReport') {
 
 sh "${mavenHome}/bin/mvn sonar:sonar"
 }     
  
  stage('UploadArtifactIntoNexus') {
 
 sh "${mavenHome}/bin/mvn deploy"
 } 
 
 stage('DeployAppIntoTomcat'){
  sh "cp $WORKSPACE/target/*.war C:\Devops\apache-tomcat-7.0.94\webapps"
  } 
  
}
