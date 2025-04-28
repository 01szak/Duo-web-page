pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git branch: 'master', url: 'https://github.com/01szak/Duo-web-page.git', credentialsId: 'GitHub Token'
            }
        }
        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }
        stage('Build') {
            steps {
                sh 'ng build --configuration production'
            }
        }
        stage('Deploy') {
            steps {
                sh 'scp -r dist/duo-web-page/* user@your-vps:/var/www/duo-web-page/'
            }
        }
    }
}
