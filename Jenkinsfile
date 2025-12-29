pipeline {
    agent any

    environment {
        IMAGE_NAME = "food-backend"
    }

    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/Danusshanji/food-delivery-devops.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                dir('Backend') {
                    bat 'docker build -t %IMAGE_NAME% .'
                }
            }
        }

        stage('Deploy using Docker Compose') {
            steps {
                dir('Backend') {
                    bat 'docker compose down'
                    bat 'docker compose up -d'
                }
            }
        }
    }
}
