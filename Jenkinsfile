pipeline{
    agent any

    stages {
        stage('delete old files') {
            steps {
                script {
                    bat "rmdir /S /Q C:\\inetpub\\wwwroot && mkdir C:\\inetpub\\wwwroot"
                }
            }
        }
    }
}
