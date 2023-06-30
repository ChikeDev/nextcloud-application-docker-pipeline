pipeline {

    tools{

        maven 'maven3.9.2'
    }
    agent any

    environment {
        registry = "722351645273.dkr.ecr.us-east-1.amazonaws.com/nextcloudapp"
    }
    stages {
        stage('Checkout') {
            steps {
                checkout scmGit(branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/ChikeDev/nextcloud-application-docker-pipeline.git']])
            }
        }
        
        stage ("Build Image") {
            steps {
                script {
                    dockerImage = docker.build registry
                    dockerImage.tag("$BUILD_NUMBER")
                }
            }
        }
        
        stage ("Push to ECR") {
            steps {
                script {
                    sh 'aws ecr get-login-password --region us-east-1 | docker login --username AWS --password-stdin 722351645273.dkr.ecr.us-east-1.amazonaws.com'
                    sh 'docker push 722351645273.dkr.ecr.us-east-1.amazonaws.com/nextcloudapp:$BUILD_NUMBER'
                    
                }
            }
        }

        stage ("run application"){
            steps{
                script {
                    sh 'docker run -d --name   sociaapp1   -p 8081:80  722351645273.dkr.ecr.us-east-1.amazonaws.com/nextcloudapp:2'
                }
            }
        }    
    }
}