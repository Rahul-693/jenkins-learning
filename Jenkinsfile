pipeline {
    agent any

    environment {
        IMAGE_NAME = "jenkins-learning"
        IMAGE_TAG = "${env.BUILD_NUMBER}"
    }

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build Docker Image') {
            steps {
                sh '''
                echo "===== Building Docker Image ====="

                docker build -t ${IMAGE_NAME}:${IMAGE_TAG} .

                echo 

                echo "===== Docker Images ====="

                docker images | grep ${IMAGE_NAME}

                '''
            }
        }
    }

    post {
        success {
            echo "Docker image built successfully."
        }

        failure {
            echo "Docker build failed."
        }
    }
}
