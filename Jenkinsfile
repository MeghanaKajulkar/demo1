pipeline {
    agent any

    environment {
        IMAGE_NAME = 'jenkins-docker-demo'
    }

    stages {
        stage('Build Docker Image') {
            steps {
                script {
                    // Build the Docker image
                    bat 'docker build -t ${IMAGE_NAME} .'
                }
            }
        }

        stage('Run Docker Container') {
            steps {
                script {
                    // Run the container
                    bat 'docker run ${IMAGE_NAME}'
                }
            }
        }

        stage('Push Docker Image') {
            steps {
                script {
                    // Push image to Docker Hub (optional)
                    bat 'docker tag ${IMAGE_NAME} yourusername/${IMAGE_NAME}'
                    bat 'docker push yourusername/${IMAGE_NAME}'
                }
            }
        }
    }
}
