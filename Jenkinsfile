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
                sh 'aws ecr get-login-password --region us-east-1 | sudo docker login --username AWS --password-stdin 303760478036.dkr.ecr.us-east-1.amazonaws.com'
            }
        }
        stage('Build') {
            steps {
                sh 'sudo docker build -t 303760478036.dkr.ecr.us-east-1.amazonaws.com/static-app:$BUILD_NUMBER .'
            }
        }
        stage('Push') {
            steps {
                sh 'sudo docker push 303760478036.dkr.ecr.us-east-1.amazonaws.com/static-app:$BUILD_NUMBER'
            }
        }
    }
}