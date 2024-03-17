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
                sh 'docker build -t my-node-app:latest .'
            }
        }

        stage('Login to Docker Hub') {         
            steps{                            
	       sh 'echo $DOCKERHUB_CREDENTIALS_PSW | sudo docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin' 
	       sh 'docker login -u $DOCKERHUB_CREDENTIALS_USR -p $DOCKERHUB_CREDENTIALS_PSW'
	       echo 'Login Completed'                
            }            
          }               
        stage('Push Image to Docker Hub') {         
            steps{                            
	        sh 'sudo docker push meghaganesh790/node:latest'                 
            echo 'Push Image Completed'       
           }           
        }      
        
        stage('Deploy') {
            steps {
                // Run Docker container
                sh 'docker run -d -p 3001:3000 my-node-app:latest'
            }
        }
    }
}
