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
                sh 'docker build -t dockerhubusername/dockerhubreponame:$BUILD_NUMBER .'
            }
        }

        stage('Login to Docker Hub & Push to Docker Hub') {         
            steps{                            
	       sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin' 
	       echo 'Login Completed'  
	       sh 'docker push dockerhubusername/dockerhubreponame:$BUILD_NUMBER'
            }            
          }               
            

        stage('Deploy') {
            steps {
                // Run Docker container
		    
                sh 'docker run -d -p 3001:3000 dockerhubusername/dockerhubreponame:latest'
            }
        }
    }
}
