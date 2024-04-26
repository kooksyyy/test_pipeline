pipeline {
    agent any

    // Replace 'your_email@example.com' with the actual email address
    environment {
        NOTIFY_EMAIL = 'kookaiisidro01@gmail.com'
    }

    stages {
        stage('Build') {
            steps {
                echo 'Building the code using Maven (replace with your build tool)'
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                echo 'Running unit tests with JUnit (replace with your test framework)'
                echo 'Running integration tests with (replace with your test framework)'
            }
            post {
                success {
                    emailext body: 'Unit and Integration Tests Passed!', subject: 'Unit & Integration Tests - $JOB_NAME - Success', to: '$NOTIFY_EMAIL', attachers: [fingerprint: true, body: 'Test Logs', filename: 'test_logs.xml' /* Replace with your log file format */]
                }
                failure {
                    emailext body: 'Unit and Integration Tests Failed!', subject: 'Unit & Integration Tests - $JOB_NAME - Failure', to: '$NOTIFY_EMAIL', attachers: [fingerprint: true, body: 'Test Logs', filename: 'test_logs.xml' /* Replace with your log file format */]
                }
            }
        }
        stage('Code Analysis') {
            steps {
                echo 'Analyzing code with SonarQube (replace with your chosen tool)'
            }
        }
        stage('Security Scan') {
            steps {
                echo 'Performing Security Scan with SAST tool (replace with your chosen tool)'
            }
            post {
                success {
                    emailext body: 'Security Scan Passed!', subject: 'Security Scan - $JOB_NAME - Success', to: '$NOTIFY_EMAIL'
                }
                failure {
                    emailext body: 'Security Scan Failed!', subject: 'Security Scan - $JOB_NAME - Failure', to: '$NOTIFY_EMAIL'
                }
            }
        }
        stage('Deploy to Staging') {
            steps {
                echo 'Deploying application to Staging environment (e.g., AWS EC2)'
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                echo 'Running integration tests on Staging environment'
            }
        }
        stage('Deploy to Production') {
            steps {
                echo 'Deploying application to Production environment (e.g., AWS EC2)'
            }
        }
    }
}
