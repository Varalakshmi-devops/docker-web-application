pipeline {
    agent any

    stages {

        stage('Clone') {
            steps {
                git branch: 'main',
                    url: 'YOUR_GITHUB_REPOSITORY_URL'
            }
        }

        stage('Build Docker Image') {
            steps {
                bat 'docker build -t devops-webapp .'
            }
        }

        stage('Stop Old Container') {
            steps {
                bat 'docker stop devops-webapp-container || exit 0'
                bat 'docker rm devops-webapp-container || exit 0'
            }
        }

        stage('Run Docker Container') {
            steps {
                bat 'docker run -d --name devops-webapp-container -p 8081:80 devops-webapp'
            }
        }
    }
}