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
        }
        stage('Code Analysis') {
            steps {
                script {
                    echo 'Analyzing the code...'

                }
            }
        }
        stage('Security Scan') {
            steps {
                script {
                    echo 'Performing security scan...'
            
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
                    echo 'Running integration tests on staging...'
    
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
            mail to: 'safymalik@yahoo.com',
                 subject: "Pipeline Success",
                 body: "The pipeline has completed successfully."
        }
        failure {
            mail to: 'safymalik@yahoo.com',
                 subject: "Pipeline Failure",
                 body: "The pipeline has failed. Please check the logs for more details."
        }
    }
}
