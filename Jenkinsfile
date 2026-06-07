pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git 'https://github.com/a250052-design/student-management-portal.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                bat 'docker build -t student-portal .'
            }
        }

        stage('Run Container') {
            steps {
                bat '''
                docker stop student-portal || exit 0
                docker rm student-portal || exit 0
                docker run -d -p 8081:80 --name student-portal student-portal
                '''
            }
        }
    }
}