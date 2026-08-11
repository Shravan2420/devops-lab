pipeline {
    agent any

    environment {
        DEPLOY_DIR = 'C:\\inetpub\\wwwroot'
    }

    stages {

        stage('Checkout') {
            steps {
                echo 'Repository checked out from GitHub'
            }
        }

        stage('Build') {
            steps {
                echo 'Build Successful'
                bat 'dir'
            }
        }

        stage('Test') {
            steps {
                echo 'Testing HTML File'
                bat 'type index.html'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying Files'

                bat '''
                xcopy /Y index.html %DEPLOY_DIR%\\
                xcopy /Y style.css %DEPLOY_DIR%\\
                xcopy /Y script.js %DEPLOY_DIR%\\
                '''
            }
        }

        stage('Run HTTP Server') {
            steps {
                echo 'Deployment completed'
            }
        }
    }

    post {
        success {
            echo 'Pipeline finished successfully!'
        }

        failure {
            echo 'Pipeline failed!'
        }
    }
}