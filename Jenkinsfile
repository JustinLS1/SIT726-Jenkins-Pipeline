pipeline {
    agent any

    environment {
        DIRECTORY_PATH = 'C:/Users/Jyols/Documents/Jenkins/SIT753 6.1C'
        TESTING_ENVIRONMENT = 'testing-environment'
        PRODUCTION_ENVIRONMENT = 'Justin'
    }
    
    stages {
        stage('Build') {
            steps {
                echo "Fetch the source code from the directory path specified by the environment variable: ${DIRECTORY_PATH}"
                echo "Compile the code and generate any necessary artifacts"
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                echo "Unit tests"
                echo "Integration tests"
            }
            post {
                success {
                    emailext body: 'The unit and integration tests have completed successfully.',
                             subject: 'Unit and Integration Tests Success',
                             to: 'jyojus@gmail.com',
                             attachLog: true
                }
                failure {
                    emailext body: 'The unit and integration tests have failed.',
                             subject: 'Unit and Integration Tests Failure',
                             to: 'jyojus@gmail.com',
                             attachLog: true
                }
            }
        }
        stage('Code Analysis') {
            steps {
                echo "Meet industry standards"
            }
        }
        stage('Security Scan') {
            steps {
                echo "Scan for vulnerabilities"
            }
            post {
                success {
                    emailext body: 'The security scan has completed successfully.',
                             subject: 'Security Scan Success',
                             to: 'jyojus@gmail.com',
                             attachLog: true
                }
                failure {
                    emailext body: 'The security scan has failed.',
                             subject: 'Security Scan Failure',
                             to: 'jyojus@gmail.com',
                             attachLog: true
                }
            }
        }
        stage('Deploy to Staging') {
            steps {
                echo "Deploy the application to a staging server"
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                echo "Ensure the application functions as expected in a production-like environment"
            }
        }
        stage('Deploy to Production') {
            steps {
                echo "Deploy the application to a production server"
            }
        }
    }
    post {
        success {
            emailext body: 'The pipeline has completed successfully.',
                     subject: 'Pipeline Success',
                     to: 'jyojus@gmail.com',
                     attachLog: true
        }
        failure {
            emailext body: 'The pipeline has failed.',
                     subject: 'Pipeline Failure',
                     to: 'jyojus@gmail.com',
                     attachLog: true
        }
    }
}
