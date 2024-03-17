pipeline {
    agent any
    environment {
    DOCKERHUB_CREDENTIALS = credentials('docker-hub-credentials-1')   
}   
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Build and Containerize') {
            steps {
                // Build Docker image
                sh 'docker build -t meghaganesh790/node:latest .'
            }
        }
        stage('Login to Docker Hub & Push to Docker Hub') {         
            steps{                            
	            sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin' 
	            echo 'Login Completed'  
	            sh 'docker push meghaganesh790/node:latest'
            }            
        }               
            

        stage('Pull Docker Image &bDeploy') {
            steps {
                // Pull Docker image from Docker Hub
                sh 'docker pull meghaganesh790/node:latest'
                sh 'docker run -d -p 3002:3000 meghaganesh790/node:latest'
            }
        }
    }
    
}
