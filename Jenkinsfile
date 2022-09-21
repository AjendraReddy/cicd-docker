pipeline {
    agent any

    stages {
        stage('checkout') {
            steps {
                git branch: 'main', url: 'git@github.com:AjendraReddy/cicd-docker.git'
            }
        }
        stage('Dockerlogin') {
            steps {
                sh 'aws ecr get-login-password --region us-east-2 | sudo docker login --username AWS --password-stdin 101275806917.dkr.ecr.us-east-2.amazonaws.com'
            }
        }
        stage('Build') {
            steps {
                sh 'sudo docker build -t 101275806917.dkr.ecr.us-east-2.amazonaws.com/cicd-docker:latest .'
            }
        }
        stage('Push') {
            steps {
                sh 'sudo docker push 101275806917.dkr.ecr.us-east-2.amazonaws.com/cicd-docker:latest'
            }
        }
    }
}