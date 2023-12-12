pipeline {
    agent any
    environment {
        DOCKER_HUB_CREDENTIALS = ''
        DOCKER_IMAGE_NAME = ';DOCKER_IMAGE_TAG = "${DOCKER_IMAGE_NAME}:${env.BUILD_NUMBER}"
 }
 stages {
 stage('Checkout') {
 steps {
 // Checkout the source code from the Git repository
 checkout scm
 }
 }
 stage('Build and Push Docker Image') {
 steps {
 script {
 // Build the Docker image
 def dockerImage = docker.build("${DOCKER_IMAGE_TAG}")
 // AuthenƟ// AuthenƟcate with Docker Hub
 docker.withRegistry('hƩps://registry.hub.docker.com', "${DOCKER_HUB_CREDENTIALS}") {
 // Push the Docker image to Docker Hub
 dockerImage.push()
 }
 }
 }
 }
 }
 post {
 success {
 echo "Docker image built and pushed successfully"
 }
 }
}