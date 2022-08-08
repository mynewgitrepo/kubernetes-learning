pipeline {
  agent any
    
    stages {      
        
        stage('Build docker image') {
           steps {
               script {         
                 def customImage = docker.build('shivangiacr210/getting-started', ".")
                 docker.withRegistry('shivangiacr210.azurecr.io', 'acr-demo') {
                 customImage.push("${env.BUILD_NUMBER}")
                 }                     
           }
        }
	  }
    }
}
