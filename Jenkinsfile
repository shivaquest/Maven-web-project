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
 checkout  'scm'
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
  sh "cp $WORKSPACE/target/*.war   \apache-tomcat-7.0.94\webapps"
  } 
  
}

