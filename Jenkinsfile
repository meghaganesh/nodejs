pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                 script {
                    git branch: 'main',
                        credentialsId: 'Credential_ID',
                        url: 'https://github.com/meghaganesh/nodejs.git'
                }
            }
        }
        
        stage('Build') {
            steps {        
                // Install dependencies and build the Node.js application
                sh 'npm install'
            }
        }
        
        stage('Containerize') {
            steps {
                // Build Docker image
                sh 'docker build -t my-node-app:latest .'
            }
        }
        
        stage('Deploy') {
            steps {
                // Run Docker container
                sh 'docker run -d -p 3000:3000 my-node-app:latest'
            }
        }
    }
}
