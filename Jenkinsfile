pipeline {
    agent any
    stages {
        stage('Cloning Git') {
            steps {
                 git credentialsId: 'jenkins-git', url: 'https://github.com/mynewgitrepo/kubernetes-learning.git'   
            }
        }
   stage('SonarQube analysis') {
     environment {
        scannerHome = tool 'sonarqube'
    }
    steps{
    
    withSonarQubeEnv('sonarqube') {
      sh "${scannerHome}/bin/sonar-scanner \
      -D sonar.projectKey=kubernetes-demo \
      -D sonar.prjectName=kubernetes-demo \
      -D sonar.projectVersion:1.0 \
      -D sonar.language:js \
      -D sonar.login=admin \
      -D sonar.password=12345678 \
      -D sonar.sources=src \
      -D sonar.host.url=http://23.96.9.202:9000/"
            }
        }
    }
        stage('build the docker images from the docker file'){
            steps{
                sh 'docker image build -t pavanktm/dockerhub:${BUILD_NUMBER} .'
            }
        }
        stage('docker login and push docker images to docker-hub') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'dockerhub', passwordVariable: 'password', usernameVariable: 'username')]) {
      
                            sh 'docker login -u ${username} -p ${password}'
                            sh 'docker image push pavanktm/dockerhub:${BUILD_NUMBER}'
                        }
            }
       }
       
        stage('deploy to dev'){
            steps{
                    script{
                        sh "cd /home/ruser && helm upgrade --set image.tag=${env.BUILD_NUMBER} -n default node-app1  ./node-app1"
                    }
                }
       
}
}
}
