
pipeline {
    agent any

    environment {
        DOCKER_IMAGE = 'my-first-web:1.0'
        DOCKER_HOST = 'tcp://docker:2375'
    }

    stages {
        stage('Checkout') {
            steps {
                echo 'Source code checked out from GitHub'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t $DOCKER_IMAGE .'
            }
        }

        stage('Verify Docker Image') {
            steps {
                sh 'docker images'
            }
        }

        stage('Deploy Container') {
            steps {
                sh '''
                    docker rm -f my-web
                    docker run -d -p 8080:80 --name my-web $DOCKER_IMAGE
                '''
            }
        }
    }
}
