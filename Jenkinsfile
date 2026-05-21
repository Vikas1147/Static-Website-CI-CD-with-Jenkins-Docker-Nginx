pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                echo 'Code Checkout'
            }
        }

        stage('Build Docker Image') {
            steps {
                bat 'docker build -t static-site .'
            }
        }

        stage('Run Container') {
            steps {
                bat 'docker run -d -p 8081:80 --name static-container static-site'
            }
        }

        stage('Smoke Test') {
            steps {
                bat 'curl http://localhost:8081'
            }
        }

        stage('Stop Container') {
            steps {
                bat 'docker stop static-container'
                bat 'docker rm static-container'
            }
        }
    }
}