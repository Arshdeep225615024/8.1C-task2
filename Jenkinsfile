pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/arshdeep225615024/8.2CDevSecOps.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Run Tests') {
            steps {
                script {
                    try {
                        sh 'npm test'
                        currentBuild.result = 'SUCCESS'
                        emailext(
                            to: 'your_email@example.com',
                            subject: "✅ TEST PASSED - ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                            body: "All tests passed successfully in stage: Run Tests",
                            attachLog: true
                        )
                    } catch (Exception e) {
                        currentBuild.result = 'FAILURE'
                        emailext(
                            to: 'your_email@example.com',
                            subject: "❌ TEST FAILED - ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                            body: "Tests failed in stage: Run Tests.\nCheck the attached logs.",
                            attachLog: true
                        )
                        throw e
                    }
                }
            }
        }

        stage('Security Scan') {
            steps {
                script {
                    try {
                        sh 'npm audit'
                        currentBuild.result = 'SUCCESS'
                        emailext(
                            to: 'your_email@example.com',
                            subject: "✅ SECURITY SCAN PASSED - ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                            body: "Security scan completed successfully in stage: Security Scan",
                            attachLog: true
                        )
                    } catch (Exception e) {
                        currentBuild.result = 'FAILURE'
                        emailext(
                            to: 'your_email@example.com',
                            subject: "❌ SECURITY SCAN FAILED - ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                            body: "Security scan failed in stage: Security Scan.\nCheck attached logs.",
                            attachLog: true
                        )
                        throw e
                    }
                }
            }
        }
    }
}

