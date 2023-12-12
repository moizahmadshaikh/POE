pipeline {
    agent any
    environment {
        DOCKER_HUB_CREDENTIALS = '7d98fc8a-5867-4dd0-b9e6-1f503062ad07'
        DOCKER_IMAGE_NAME = 'moizshaikh/imageforpoe'
        DOCKER_IMAGE_TAG = "${DOCKER_IMAGE_NAME}:${env.BUILD_NUMBER}"
        }
        stages {
            stage('Checkout') {
                steps {
                    checkout scm
                    }
                }
            stage('Build and Push Docker Image') {
                steps {
                    script {

                        def dockerImage = docker.build("${DOCKER_IMAGE_TAG}")

                        docker.withRegistry('https://registry.hub.docker.com', "${DOCKER_HUB_CREDENTIALS}") {

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
