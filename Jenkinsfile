pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
    
        
        stage('Build and Containerize') {
            steps {
                // Build Docker image
                sh 'docker build -t my-node-app:v2 .'
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
