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

        stage('Push Docker Image') {
            steps {
                withCredentials([usernamePassword(
                    credentialsId: 'dockerhub-creds',
                    usernameVariable: 'DOCKER_USER',
                    passwordVariable: 'DOCKER_PASS'
                )]) {

                    sh '''
                        echo "$DOCKER_PASS" | docker login -u "$DOCKER_USER" --password-stdin

                        docker tag jenkins-learning:${BUILD_NUMBER} $DOCKER_USER/jenkins-learning:${BUILD_NUMBER}

                        docker push $DOCKER_USER/jenkins-learning:${BUILD_NUMBER}

                        docker logout
                    '''
                }
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
