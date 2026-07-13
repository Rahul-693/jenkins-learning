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
                    docker build -t jenkins-learning:${BUILD_NUMBER} .
                '''
            }
        }

        stage('Push Docker Image to ECR') {
            steps {
                sh '''
                    aws ecr get-login-password --region ap-south-2 \
                    | docker login \
                    --username AWS \
                    --password-stdin 568256616486.dkr.ecr.ap-south-2.amazonaws.com

                    docker tag jenkins-learning:${BUILD_NUMBER} \
                    568256616486.dkr.ecr.ap-south-2.amazonaws.com/jenkins-learning:${BUILD_NUMBER}

                    docker push \
                    568256616486.dkr.ecr.ap-south-2.amazonaws.com/jenkins-learning:${BUILD_NUMBER}

                    docker logout 568256616486.dkr.ecr.ap-south-2.amazonaws.com
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
