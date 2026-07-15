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
		
		stage('Download Task Definition') {
            steps {
                sh '''
                aws ecs describe-task-definition \
                  --task-definition jenkins-learning-task \
                  --region ap-south-2 \
                  --query taskDefinition \
                  > task-definition.json
                '''
            }
        }
		
		stage('Prepare Task Definition') {
            steps {
                sh '''
                jq 'del(
                    .taskDefinitionArn,
                    .revision,
                    .status,
                    .registeredAt,
                    .registeredBy,
                    .compatibilities,
                    .requiresAttributes
                )' task-definition.json > new-task-definition.json
                '''
            }
        }
		
		stage('Update Image') {
            steps {
                sh '''
				jq --arg IMAGE "568256616486.dkr.ecr.ap-south-2.amazonaws.com/jenkins-learning:$BUILD_NUMBER" \
                '(.containerDefinitions[] | select(.name=="jenkins-container")).image = $IMAGE' \
                new-task-definition.json > final-task-definition.json
                '''
            }
        }
		
		stage('Register Task Definition') {
            steps {
                sh '''
                aws ecs register-task-definition \
                  --region ap-south-2 \
                  --cli-input-json file://final-task-definition.json
                '''
            }
        }
		
		stage('Deploy to ECS') {
            steps {
                sh '''
                aws ecs update-service \
                  --cluster jenkins-learning-cluster \
                  --service jenkins-learning-service \
                  --task-definition jenkins-learning-task \
                  --force-new-deployment \
                  --region ap-south-2

			    aws ecs wait services-stable \
                  --cluster jenkins-learning-cluster \
                  --services jenkins-learning-service \
                  --region ap-south-2 
                '''
            }
        }
    }
 
    post {
        success {
            echo "Deployment successfully."
        }
    
        failure {
            echo "Deployment failed."
        }

		always {
			echo "Cleaning Docker ..."

			sh '''
			    docker image prune -af
				docker builder prune -af
			'''
		}
    }
}
