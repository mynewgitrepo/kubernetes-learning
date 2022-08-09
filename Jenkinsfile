pipeline {
  agent any
  stages {      
        
   stage('SonarQube analysis') {
    steps{
    def scannerHome =  tool 'sonarqube';
    withSonarQubeEnv('sonarqube') {
      sh "${scannerHome}/bin/sonar-scanner \
      -D sonar.login=admin \
      -D sonar.password=admin \
      -D sonar.projectKey=sonarqubetest \
      -D sonar.host.url=http://20.124.22.207/"
    }
  }
  }
    }
}

