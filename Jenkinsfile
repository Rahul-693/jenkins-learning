pipeline {

    agent any

    stages {

        stage('Demo') {

            steps {

                sh '''

                echo "Running Build"

                pwd

                ls unknown_directory

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
