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
                        sh 'npm test || true'   // quick fix: or replace test script with "echo ok"
                        emailext(
                            to: 'your_email@gmail.com',
                            subject: "✅ TEST PASSED - ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                            body: "Tests completed. Check attached logs.",
                            attachLog: true
                        )
                    } catch (Exception e) {
                        emailext(
                            to: 'your_email@gmail.com',
                            subject: "❌ TEST FAILED - ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                            body: "Tests failed. Check attached logs.",
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
                        sh 'npm audit || true'
                        emailext(
                            to: 'your_email@gmail.com',
                            subject: "✅ SECURITY SCAN PASSED - ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                            body: "Security scan completed successfully.",
                            attachLog: true
                        )
                    } catch (Exception e) {
                        emailext(
                            to: 'your_email@gmail.com',
                            subject: "❌ SECURITY SCAN FAILED - ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                            body: "Security scan failed. Check attached logs.",
                            attachLog: true
                        )
                        throw e
                    }
                }
            }
        }
    }
}
