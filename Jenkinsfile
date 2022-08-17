pipeline {
    agent any 
    stages {
        
        stage('SonarQube analysis') {
            environment {
                scannerHome = tool 'sonarqube'
            }
               
        stage('chechout') { 
            steps {
                git 'https://github.com/mynewgitrepo/kubernetes-learning.git' 
            }
        }
        stage('Test') { 
            steps {
                sh 'pwd' 
            }
        }
        stage('Deploy') { 
            steps {
                sh 'pwd'
            }
        }
    }
}
