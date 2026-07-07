pipeline {

    agent any

    stages {

        stage('Jenkins Information') {
            steps {

                echo "Job Name : ${env.JOB_NAME}"

                echo "Build Number : ${env.BUILD_NUMBER}"

                echo "Workspace : ${env.WORKSPACE}"

                echo "Jenkins URL : ${env.JENKINS_URL}"

            }
        }

        stage('Shell Variables') {
            steps {

                sh '''
                echo "Job Name = $JOB_NAME"
                echo "Build Number = $BUILD_NUMBER"
                echo "Workspace = $WORKSPACE"
                '''

            }
        }

    }

}
