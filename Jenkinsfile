pipeline {
    agent any
    stages {
        stage('Git Checkout') {
            steps {
                script {
                    git branch: 'main',
                        credentialsId: 'Credential_ID',
                        url: 'https://github.com/meghaganesh/nodejs.git'
                }
            }
        }
    }
}
        
