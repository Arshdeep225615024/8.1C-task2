pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Running build stage...'
                sh 'echo Build completed'
            }
            post {
                success {
                    mail to: 'arshdeep932985@gmail.com',
                         subject: "SUCCESS: Build Stage - Job ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                         body: "The Build stage completed successfully.\nCheck Jenkins for logs."
                }
                failure {
                    mail to: 'arshdeep932985@gmail.com',
                         subject: "FAILED: Build Stage - Job ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                         body: "The Build stage failed.\nCheck Jenkins for details."
                }
            }
        }

        stage('Test') {
            steps {
                echo 'Running test stage...'
                sh 'exit 1' // force failure to test emails
            }
            post {
                success {
                    mail to: 'arshdeep932985@gmail.com',
                         subject: "SUCCESS: Test Stage - Job ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                         body: "The Test stage completed successfully.\nCheck Jenkins for logs."
                }
                failure {
                    mail to: 'arshdeep932985@gmail.com',
                         subject: "FAILED: Test Stage - Job ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                         body: "The Test stage failed.\nCheck Jenkins for details."
                }
            }
        }
    }

    post {
        always {
            mail to: 'arshdeep932985@gmail.com',
                 subject: "Pipeline Finished - ${currentBuild.currentResult} - Job ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                 body: "Pipeline finished with status: ${currentBuild.currentResult}.\n\nCheck console output for more details."
        }
    }
}
