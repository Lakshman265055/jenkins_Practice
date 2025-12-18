pipeline {
    agent {
        label 'agent-1'
    } // This runs the entire pipeline on any available agent
     options{
        timeout(time: 10, unit: 'MINUTES')
        disableConcurrentBuilds()
        timestamps()
        retry(1)
    }

    parameters {
        string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')
        text(name: 'BIOGRAPHY', defaultValue: '', description: 'Enter some information about the person')

        booleanParam(name: 'TOGGLE', defaultValue: true, description: 'Toggle this value')

        choice(name: 'CHOICE', choices: ['One', 'Two', 'Three'], description: 'Pick something')

        password(name: 'PASSWORD', defaultValue: 'SECRET', description: 'Enter a password')
    } 
    stages {
        stage('Build') {
            steps {
                echo 'Building the application...'

                //echo "this is build number ${BUILD_NUMBER}"
                sh "echo this shell is ${WORKSPACE}"
                
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
        stage('Print Params'){
            steps{
                sh "echo Hello ${PERSON}"
                echo "Biography: ${params.BIOGRAPHY}"
                echo "Toggle: ${params.TOGGLE}"
                echo "Choice: ${params.CHOICE}"
                echo "Password: ${params.PASSWORD}"  
            }
        }
        stage('Approval') {
      input {
         message "Approve deployment?"
         submitter "admin"
  }
  steps {
    sh 'echo Approved'
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
