pipeline {
    agent any 
    stages {
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
