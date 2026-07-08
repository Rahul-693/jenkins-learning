pipeline {

    agent any

    parameters {

        choice(
            name: 'ENVIRONMENT',
            choices: ['DEV', 'QA', 'UAT', 'PROD'],
            description: 'Choose deployment environment'
        )

    }

    stages {

        stage('Show Environment') {

            steps {

                echo "Selected Environment: ${params.ENVIRONMENT}"

            }

        }

    }

}
