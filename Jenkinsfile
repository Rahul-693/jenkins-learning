pipeline {
    agent any

    stages {

        stage('Welcome') {
            steps {
                echo 'Hello Rahul!'
            }
        }

        stage('Current Directory') {
            steps {
                sh 'pwd'
            }
        }

        stage('List Files') {
            steps {
                sh 'ls -la'
            }
        }

    }
}
