pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
            tool 'Maven'
        }
        stage('Unit and Integration Tests') {
            steps {
                sh 'mvn test'
            }
            tool 'JUnit'
        }
        stage('Code Analysis') {
            steps {
                sh 'sonar-scanner'
            }
            tool 'SonarQube'
        }
        stage('Security Scan') {
            steps {
                sh 'owasp-zap'
            }
            tool 'OWASP ZAP'
        }
        stage('Deploy to Staging') {
            steps {
                sh 'aws deploy push --application-name jenkins-pipeline-demo --s3-bucket my-bucket'
            }
            tool 'AWS CLI'
        }
        stage('Integration Tests on Staging') {
            steps {
                sh 'mvn test'
            }
            tool 'JUnit'
        }
        stage('Deploy to Production') {
            steps {
                sh 'aws deploy push --application-name jenkins-pipeline-demo --s3-bucket my-bucket'
            }
            tool 'AWS CLI'
        }
    }
    post {
        success {
            mail to: 'your-email@example.com',
                 subject: 'Pipeline Success',
                 body: 'The pipeline has completed successfully.',
                 attachLog: true
        }
        failure {
            mail to: 'your-email@example.com',
                 subject: 'Pipeline Failure',
                 body: 'The pipeline has failed.',
                 attachLog: true
        }
    }
}
