pipeline {
    agent{
        docker{
            image 'node:24-alpine' //Image Docker Node.js
            args '-p 5001:5001'
        }
    }
    environment {
        HOME = '/tmp'
        npm_config_cache = '/tmp/.npm'
    }
    
    stages {        
        stage('Install Dependencies') {
            steps {
                
                sh 'npm install'
            }
        }
        stage('Build') {
            steps {
                
                echo 'Building the application...'
            }
        }
        stage('Test') {
            steps {
                
                sh 'npm test'
            }
        }
        stage('Run Application') {
            steps {
                // Execute the app
                sh 'npm start &'
                // wait 5 seconds to start appp
                sh 'sleep 60'
            }
        }
    }
    post {
        always {
            echo 'Cleaning up...'
        }
        success {
            echo 'Pipeline succeeded!'
        }
        failure {
            echo 'Pipeline failed!'
        }
    }
}




















