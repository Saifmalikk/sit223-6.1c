pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                script {
                    echo 'Building the code...'
                }
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                script {
                    echo 'Running unit and integration tests...'
                }
            }
            post {
                success {
                    emailext to: 'safymalik@yahoo.com',
                            subject: "Unit and Integration Tests Passed",
                            body: "All unit and integration tests have passed successfully."
                }
                failure {
                    emailext to: 'safymalik@yahoo.com',
                            subject: "Unit and Integration Tests Failed",
                            body: "Some unit or integration tests have failed. Please check the logs for more details."
                }
            }
        }
        stage('Code Analysis') {
            steps {
                script {
                    echo 'Analyzing the code...'
                }
            }
        }
        stage('Deploy to Staging') {
            steps {
                script {
                    echo 'Deploying to staging server...'
                }
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                script {
                    echo 'Running integration tests on staging environment...'
                }
            }
        }
        stage('Deploy to Production') {
            steps {
                script {
                    echo 'Deploying to production server...'
                }
            }
        }
    }
    post {
        success {
            emailext to: 'safymalik@yahoo.com',
                    subject: "Pipeline Success",
                    body: "The pipeline completed successfully."
        }
        failure {
            emailext to: 'safymalik@yahoo.com',
                    subject: "Pipeline Failure",
                    body: "The pipeline failed. Please check the logs for more details."
        }
    }
}
