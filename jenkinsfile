pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'mvn clean install' 
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                sh 'mvn test'  
            }
            post {
                success {
                    emailext subject: 'Test Stage Success',
                              body: 'The test stage has passed successfully.',
                              attachLog: true,
                              to: 'sohanreddy58@gmail.com'
                }
                failure {
                    emailext subject: 'Test Stage Failed',
                              body: 'The test stage has failed. Please check the build log.',
                              attachLog: true,
                              to: 'sohanreddy58@gmail.com'
                }
            }
        }
        stage('Code Analysis') {
            steps {
                sh 'your-analysis-tool-command'  
            }
        }
        stage('Security Scan') {
            steps {
                sh 'your-security-scan-tool-command'  
            }
            post {
                success {
                    emailext subject: 'Security Scan Stage Success',
                              body: 'The security scan stage has passed successfully.',
                              attachLog: true,
                              to: 'sohanreddy58@gmail.com'
                }
                failure {
                    emailext subject: 'Security Scan Stage Failed',
                              body: 'The security scan stage has failed. Please check the build log.',
                              attachLog: true,
                              to: 'sohanreddy58@gmail.com'
                }
            }
        }
        stage('Deploy to Staging') {
            steps {
                sh 'your-deployment-command-for-staging'  
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                sh 'your-integration-tests-command-for-staging'  
            }
        }
        stage('Deploy to Production') {
            steps {
                sh 'your-deployment-command-for-production'  
            }
        }
    }
}
