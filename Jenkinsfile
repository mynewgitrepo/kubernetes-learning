pipeline {
  agent any
    
    stages {      
        
        stage('Build docker image') {
           steps {
               script {         
                 def customImage = docker.build('shivangiacr210.azurecr.io/getting-started', ".")
                 docker.withRegistry('https://shivangiacr210.azurecr.io', 'acr-demo') {
                 customImage.push("${env.BUILD_NUMBER}")
                 }                     
           }
        }
	  }
	    	    
	  stage('Build on k8 ') {
            steps {           
                        sh 'pwd'
                        sh 'helm list'
		        		
            }           
        }
    }
}
