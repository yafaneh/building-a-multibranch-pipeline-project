pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                bat 'echo "Hello world!"'
            }
        }
        stage('Test') {
            steps {
                bat '/jenkins/scripts/test.bat'
            }
        }
        stage('Deliver for development') {
            when {
                branch 'development'
            }
            steps {
                bat '/jenkins/scripts/deliver-for-development.bat'
                input message: 'Finished using the web site? (Click "Proceed" to continue)'
                bat '/jenkins/scripts/kill.bat'
            }
        }
        stage('Deploy for production') {
            when {
                branch 'production'
            }
            steps {
                bat '/jenkins/scripts/deploy-for-production.bat'
                input message: 'Finished using the web site? (Click "Proceed" to continue)'
                bat '/jenkins/scripts/kill.bat'
            }
        }
    }
}
