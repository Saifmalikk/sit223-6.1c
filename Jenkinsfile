pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                script {
                    // Capture the output of the build step into a log file
                    echo 'Building the code using Maven or Gradle...' | tee 'build.log'
                }
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                script {
                    // Capture the output of unit and integration tests into a log file
                    echo 'Running unit and integration tests using JUnit or TestNG...' | tee 'unit-tests.log'
                }
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
                script {
                    // Capture code analysis output
                    echo 'Analyzing the code using SonarQube or Checkstyle...' | tee 'code-analysis.log'
                }
            }
        }
        stage('Security Scan') {
            steps {
                script {
                    // Capture security scan output
                    echo 'Performing security scan using OWASP ZAP or Fortify...' | tee 'security-scan.log'
                }
            }
            post {
                success {
                    emailext to: 'safymalik@yahoo.com',
                            subject: "Security Scan Success",
                            body: "Security scan completed successfully without critical issues.",
                            attachmentsPattern: '**/security-scan.log'  // Attach security scan log file
                }
                failure {
                    emailext to: 'safymalik@yahoo.com',
                            subject: "Security Scan Failure",
                            body: "Security scan has identified issues. Please review the scan results.",
                            attachmentsPattern: '**/security-scan.log'  // Attach security scan log file
                }
            }
        }
        stage('Deploy to Staging') {
            steps {
                script {
                    // Capture deploy output
                    echo 'Deploying to staging server using Docker or Kubernetes...' | tee 'deploy-staging.log'
                }
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                script {
                    echo 'Running integration tests on staging environment...' | tee 'integration-tests-staging.log'
                }
            }
        }
        stage('Deploy to Production') {
            steps {
                script {
                    echo 'Deploying to production server using Docker or Kubernetes...' | tee 'deploy-production.log'
                }
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
