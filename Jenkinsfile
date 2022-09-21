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
                sh 'aws ecr-public get-login-password --region us-east-1 | sudo docker login --username AWS --password-stdin public.ecr.aws/m2l2s8v4'
            }
        }
        stage('Build') {
            steps {
                sh 'sudo docker build -t latest public.ecr.aws/m2l2s8v4/cicddocker:latest'
            }
        }
        stage('Push') {
            steps {
                sh 'sudo docker push public.ecr.aws/m2l2s8v4/cicddocker:latest'
            }
        }
    }
}