pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Running build stage...'
                sh 'echo "Build completed"'
            }
            post {
                always {
                    emailext(
                        to: "arshdeep932985@gmail.com",
                        subject: "Build Stage - ${currentBuild.currentResult}",
                        body: """Hello Team,<br><br>
                                The <b>Build</b> stage has completed.<br>
                                Status: ${currentBuild.currentResult}<br>
                                Build Number: ${env.BUILD_NUMBER}<br>
                                Job: ${env.JOB_NAME}<br><br>
                                Regards,<br>
                                Jenkins"""
                    )
                }
            }
        }

        stage('Test') {
            steps {
                echo 'Running test stage...'
                sh 'exit 1'  // Force a failure to test "FAILURE" emails
            }
            post {
                always {
                    emailext(
                        to: "arshdeep932985@gmail.com",
                        subject: "Test Stage - ${currentBuild.currentResult}",
                        body: """Hello Team,<br><br>
                                The <b>Test</b> stage has completed.<br>
                                Status: ${currentBuild.currentResult}<br>
                                Build Number: ${env.BUILD_NUMBER}<br>
                                Job: ${env.JOB_NAME}<br><br>
                                Regards,<br>
                                Jenkins"""
                    )
                }
            }
        }
    }

    post {
        always {
            emailext(
                to: "arshdeep932985@gmail.com",
                subject: "Pipeline Completed - ${currentBuild.currentResult}",
                body: """Hello Team,<br><br>
                        The <b>Pipeline</b> has finished.<br>
                        Status: ${currentBuild.currentResult}<br>
                        Build Number: ${env.BUILD_NUMBER}<br>
                        Job: ${env.JOB_NAME}<br><br>
                        Regards,<br>
                        Jenkins"""
            )
        }
    }
}

