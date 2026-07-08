pipeline {

    agent any

    stages {

        stage('Pipeline Failure Demo') {

            steps {

                sh '''

                echo "Step 1"

                pwd

                echo "Step 2"

                ls does_not_exist

                echo "Step 3"

                '''

            }

        }

    }

}
