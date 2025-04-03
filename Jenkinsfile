pipeline {
    agent any
    environment {
        // Update these values with your Docker Hub info
        DOCKER_IMAGE = "filipjovanovski1/blue-ocean-image"
        DOCKER_TAG = "latest"
    }
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t filipjovanovski1/blue-ocean-image:latest .'
            }
        }
        stage('Push Docker Image') {
            steps {
                withDockerRegistry([credentialsId: 'dockerhub', url: '']) {
                    sh 'docker push filipjovanovski1/blue-ocean-image:latest'
                }
            }
        }
    }
}
