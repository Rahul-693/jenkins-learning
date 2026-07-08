pipeline {

    agent any

    stages {

        stage('Demo') {

            steps {

                sh '''

                echo "Running Build"

                pwd

                '''

            }

        }

    }

    post {

        always {

            echo "This always executes."

        }

        success {

            echo "Pipeline completed successfully."

        }

        failure {

            echo "Pipeline failed."

        }

    }

}
