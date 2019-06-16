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
	stage('UploadArtifactIntoNexus') {
 
          bat   'mvn deploy'
        } 

	
	
}
