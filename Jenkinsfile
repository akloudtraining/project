pipeline {
    agent any
    environment{
     registry = "a330167320139.dkr.ecr.us-east-1.amazonaws.com/nodejs-app"
    }
    stages {
        stage('Build') {
            steps {
                sh 'docker build -t 330167320139.dkr.ecr.us-east-1.amazonaws.com/nodejs-app:1.0.2 .'
            }
        }
        stage('Login') {
            steps {
                sh 'aws ecr get-login-password --region us-east-1 | docker login --username AWS --password-stdin 330167320139.dkr.ecr.us-east-1.amazonaws.com'
            }
        }
        stage('Push') {
            steps {
                sh 'docker push  330167320139.dkr.ecr.us-east-1.amazonaws.com/nodejs-app:1.0.2'
            }
        }
        stage('Logout') {
            steps {
                sh 'docker logout'
            }
        }
    }
}