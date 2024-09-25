pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                // Use the shell (sh) command to redirect the output to 'build.log'
                sh '''
                echo "Building the code using Maven or Gradle..." > build.log
                '''
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                // Capture the output of unit and integration tests into 'unit-tests.log'
                sh '''
                echo "Running unit and integration tests using JUnit or TestNG..." > unit-tests.log
                '''
            }
            post {
                success {
                    emailext to: 'safymalik@yahoo.com',
                            subject: "Unit and Integration Tests Success",
                            body: "All unit and integration tests have passed.",
                            attachmentsPattern: '**/unit-tests.log'  // Attach log file
                }
                failure {
                    emailext to: 'safymalik@yahoo.com',
                            subject: "Unit and Integration Tests Failure",
                            body: "Some unit or integration tests have failed. Please check the logs for more details.",
                            attachmentsPattern: '**/unit-tests.log'  // Attach log file
                }
            }
        }
        stage('Code Analysis') {
            steps {
                // Capture code analysis output into 'code-analysis.log'
                sh '''
                echo "Analyzing the code using SonarQube or Checkstyle..." > code-analysis.log
                '''
            }
        }
        stage('Security Scan') {
            steps {
                // Capture security scan output into 'security-scan.log'
                sh '''
                echo "Performing security scan using OWASP ZAP or Fortify..." > security-scan.log
                '''
            }
            post {
                success {
                    emailext to: 'safymalik@yahoo.com',
                            subject: "Security Scan Success",
                            body: "Security scan completed successfully without critical issues.",
                            attachmentsPattern: '**/security-scan.log'  // Attach log file
                }
                failure {
                    emailext to: 'safymalik@yahoo.com',
                            subject: "Security Scan Failure",
                            body: "Security scan has identified issues. Please review the scan results.",
                            attachmentsPattern: '**/security-scan.log'  // Attach log file
                }
            }
        }
        stage('Deploy to Staging') {
            steps {
                // Capture deploy output into 'deploy-staging.log'
                sh '''
                echo "Deploying to staging server using Docker or Kubernetes..." > deploy-staging.log
                '''
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                sh '''
                echo "Running integration tests on staging environment..." > integration-tests-staging.log
                '''
            }
        }
        stage('Deploy to Production') {
            steps {
                sh '''
                echo "Deploying to production server using Docker or Kubernetes..." > deploy-production.log
                '''
            }
        }
    }
    post {
        success {
            emailext to: 'safymalik@yahoo.com',
                    subject: "Pipeline Complete Success",
                    body: "The entire pipeline has completed successfully and the application is now in production.",
                    attachmentsPattern: '**/*.log'  // Attach all log files
        }
        failure {
            emailext to: 'safymalik@yahoo.com',
                    subject: "Pipeline Complete Failure",
                    body: "The pipeline has encountered a failure in one of its stages. Please check the logs for more details.",
                    attachmentsPattern: '**/*.log'  // Attach all log files
        }
    }
}
