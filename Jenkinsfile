pipeline {
    agent any

    environment {
        IMAGE_NAME = "flask-docker-app"
        CONTAINER_NAME = "flask_app"
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/amitnaik96/flask-docker-app.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                bat 'docker build -t flask-docker-app .'
            }
        }

        stage('Run Docker Container') {
            steps {
                bat 'docker stop flask_app || true'
                bat 'docker rm flask_app || true'
                bat 'docker run -d -p 5000:5000 --name flask_app flask-docker-app'
            }
        }

        stage('Cleanup') {
            steps {
                bat 'docker image prune -f'
            }
        }
    }
}
