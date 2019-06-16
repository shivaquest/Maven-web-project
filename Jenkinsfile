#!groovy

node {
  
	   
       stage('Checkout'){

          checkout scm
       }

       stage('Compiling'){

          bat 'mvn install'
       }
	   
      stage('testing') {
                   
                    bat  'mvn test'
                }
       
	stage('package'){
	   bat  'mvn package'
	}
	stage('deploy into Tomcat'){
	   sh 'cp \workspace\Testing pipeline\target\maven-web-project-1.0-SNAPSHOT.war  TOMCAT_DIRECTORY/webapps/'
	}
	
	
}
