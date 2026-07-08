pipeline {

    agent any

    stages {

        stage('Script Block Demo') {

            steps {

                script {

                    def student = "Rahul"

                    def course = "DevOps"

                    echo "Student : ${student}"

                    echo "Course : ${course}"

                }

            }

        }

        stage('Build Decision') {

            steps {

                script {

                    if(env.BUILD_NUMBER.toInteger() % 2 == 0){

                        echo "Even Build Number"

                    } else {

                        echo "Odd Build Number"

                    }

                }

            }

        }

    }

}
