pipeline {
  agent any
    stages {      
        
   stage('SonarQube analysis') {
     environment {
        scannerHome = tool 'sonarqube'
    }
    steps{
    
    withSonarQubeEnv('sonarqube') {
      sh "${scannerHome}/bin/sonar-scanner \
      -D sonar.login=admin \
      -D sonar.password=admin1 \
      -D sonar.projectKey=test \
      -D sonar.host.url=http://20.124.22.207:9000/"
    }
  }
  }
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
    }
}

