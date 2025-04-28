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
           script {
               // Dodanie klucza SSH do zaufanych hostów
               sh 'ssh-keyscan -H 57.128.227.137 >> ~/.ssh/known_hosts'

               // Wykonanie SCP w celu przesłania plików na serwer
               sh 'scp -r dist/duo-web-page/3rdpartylicenses.txt dist/duo-web-page/browser dist/duo-web-page/prerendered-routes.json kacper@57.128.227.137:/var/www/duo-web-page/'
           }
       }
   }

    }
}
