node {
        
        

  stage('SonarQube analysis') {
    def scannerHome = tool 'sonarqube';
    withSonarQubeEnv('sonarqube') {
      sh "${scannerHome}/bin/sonar-scanner \
      -D sonar.login=admin \
      -D sonar.password=admin1 \
      -D sonar.projectKey=test \
      -D sonar.host.url=http://20.124.22.207:9000/"
    }
  }

    }

