pipeline {
    agent any // This runs the entire pipeline on any available agent
    stages {
        stage('Build') {
            steps {
                echo 'Building the application...'

                //echo "this is build number ${BUILD_NUMBER}"
                sh "echo this shell is ${WORKSPACE}"

                echo " this is groovy style ${env.WORKSPACE}"
                
                // Replace with your build commands, e.g., sh 'make' or sh 'mvn clean install'
            }
        }
        stage('Test') {
            steps {
                echo 'Running tests...'
                // Replace with your test commands, e.g., sh 'make check'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying the application...'
                // Replace with your deployment commands
            }
        }
    }
    post {
        always {
            echo 'I will always run, regardless of the build status.' // Runs after every stage evaluation
        }
        success {
            echo 'The pipeline succeeded!'
        }
        failure {
            echo 'The pipeline failed!'
        }
    }
}
