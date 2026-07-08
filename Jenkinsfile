pipeline {

    agent any

    stages {

        stage('Shell Script Demo') {

            steps {

                sh '''

                echo "===== User ====="
                whoami

                echo

                echo "===== Directory ====="
                pwd

                echo

                echo "===== Files ====="
                ls -la

                echo

                echo "===== Date ====="
                date

                echo

                echo "===== Java ====="
                java --version

                '''

            }

        }

    }

}
