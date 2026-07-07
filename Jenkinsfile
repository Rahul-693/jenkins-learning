pipeline {

    agent any

    environment {
        STUDENT = "Rahul"
        COURSE = "DevOps"
        COMPANY = "OpenAI Training Lab"
        VERSION = "1.0"
    }

    stages {

        stage('Built-in Variables') {
            steps {
                echo "Job Name      : ${env.JOB_NAME}"
                echo "Build Number  : ${env.BUILD_NUMBER}"
                echo "Workspace     : ${env.WORKSPACE}"
            }
        }

        stage('Custom Variables') {
            steps {
                echo "Student : ${STUDENT}"
                echo "Course  : ${COURSE}"
                echo "Version : ${VERSION}"
            }
        }

        stage('Shell Access') {
            steps {
                sh '''
                echo "Student = $STUDENT"
                echo "Course = $COURSE"
                echo "Version = $VERSION"
                '''
            }
        }

    }
}
