pipeline {
    agent any

    stages {

        stage('Build Image') {
            steps {
                bat 'docker build -t static-site .'
            }
        }

        stage('Run Container') {
            steps {
                bat 'docker run -d -p 8081:80 --name static-container static-site'
            }
        }

        stage('Check Site') {
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