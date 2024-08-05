pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                script {
                    echo 'Building the code...'
                    // Example: sh 'mvn clean package'
                }
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                script {
                    echo 'Running unit and integration tests...'
                    // Example: sh 'mvn test'
                }
            }
        }
        stage('Code Analysis') {
            steps {
                script {
                    echo 'Analyzing the code...'
                    // Example: sh 'sonar-scanner'
                }
            }
        }
        stage('Security Scan') {
            steps {
                script {
                    echo 'Performing security scan...'
                    // Example: sh 'npm audit'
                }
            }
        }
        stage('Deploy to Staging') {
            steps {
                script {
                    echo 'Deploying to staging server...'
                    // Example: sh 'deploy-script.sh'
                }
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                script {
                    echo 'Running integration tests on staging...'
                    // Example: sh 'integration-test-script.sh'
                }
            }
        }
        stage('Deploy to Production') {
            steps {
                script {
                    echo 'Deploying to production server...'
                    // Example: sh 'deploy-script.sh'
                }
            }
        }
    }

    post {
        success {
            mail to: 'developer@example.com',
                 subject: "Pipeline Success",
                 body: "The pipeline has completed successfully."
        }
        failure {
            mail to: 'developer@example.com',
                 subject: "Pipeline Failure",
                 body: "The pipeline has failed. Please check the logs for more details."
        }
    }
}
