pipeline {
    agent any
    environment {
        DEPLOY_DIR = 'C:\\inetpub\\wwwroot' // IIS web root folder
    }
    stages {
    stage('Checkout') {
    steps {
        echo 'Cloning project from GitHub...'
        git branch: 'main', url: 'https://github.com/Shravan2420/devops-lab.git'
    }
    }
    stage('Build') {
    steps {
        echo 'Build Successful'
        bat 'dir'
    }
    }
    stage('Deploy') {
        steps {
            echo 'Deploying Files to IIS'

            bat '''
            xcopy /Y index.html %DEPLOY_DIR%\\
            xcopy /Y style.css %DEPLOY_DIR%\\
            xcopy /Y script.js %DEPLOY_DIR%\\
        '''
        }
    }
    }
    stage('Run HTTP Server (Optional Test)') {
        steps {
            echo 'Skipping HTTP server (use IIS instead)'
 // For testing, you can use: bat 'python -m http.server 8000'
        }
    }
 
    post {
    success {
        echo 'Pipeline finished successfully! Visit: http://localhost/index.html'
    }
    failure {
        echo 'Pipeline failed! Check build logs.'
    }
    }
}