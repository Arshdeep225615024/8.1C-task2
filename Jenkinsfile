pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Running build stage...'
                mail to: 'arshdeep932985@gmail.com',
                     subject: "Build completed - ${currentBuild.currentResult}",
                     body: "Hello,\n\nThe build stage finished with status: ${currentBuild.currentResult}.\nBuild: ${env.BUILD_NUMBER}\nJob: ${env.JOB_NAME}\n\nRegards,\nJenkins"
            }
        }
    }
}
