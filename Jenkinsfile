pipeline {
    agent any

    stages {

        stage('Build Docker Image') {
            steps {
                bat 'docker build -t student-portal .'
            }
        }

        stage('Run Container') {
            steps {
                bat '''
                docker stop student-portal >nul 2>&1
                docker rm student-portal >nul 2>&1
                docker run -d -p 8081:80 --name student-portal student-portal
                '''
            }
        }
    }
}