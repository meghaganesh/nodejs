pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        
        stage('Build') {
            steps {   
                sh 'curl -sL https://deb.nodesource.com/setup_14.x | bash -'
                sh 'apt-get install -y nodejs'
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
