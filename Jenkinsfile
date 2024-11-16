pipeline {
    agent any

    environment {
        IMAGE_NAME = 'jenkins-docker-demo'
        DOCKER_CREDENTIALS_ID = 'docker-hub-credentials-id'  // Replace with the actual Jenkins credential ID
    }

    stages {
        stage('Login to Docker Hub') {
            steps {
                script {
                    // Securely login to Docker Hub using Jenkins credentials
                    withCredentials([usernamePassword(credentialsId:'33f08673-7e3e-4bd8-b0be-0b775963893f', 
                                                        usernameVariable: 'DOCKER_USER', 
                                                        passwordVariable: 'DOCKER_PASS')]) {
                        bat 'docker login -u %DOCKER_USER% -p %DOCKER_PASS%'
                    }
                }
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    // Build the Docker image
                    bat "docker build -t %IMAGE_NAME% ."
                }
            }
        }

        stage('Run Docker Container') {
            steps {
                script {
                    // Run the container
                    bat "docker run %IMAGE_NAME%"
                }
            }
        }

        stage('Push Docker Image') {
            steps {
                script {
                    // Tag and push the image to Docker Hub
                    bat "docker tag %IMAGE_NAME% yourusername/%IMAGE_NAME%"
                    bat "docker push yourusername/%IMAGE_NAME%"
                }
            }
        }
    }
}
