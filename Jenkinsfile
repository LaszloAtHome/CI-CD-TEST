pipeline{
    agent any

    stages {
      stage('npm install') {
            steps {
                script {
                    bat "npm i -f"
                }
            }
        }
        stage('build angular app') {
            steps {
                script {
                    bat "ng build --configuration=production --output-path dist"
                }
            }
        }
        stage('delete old files') {
            steps {
                script {
                    bat "del /S C:\\inetpub\\wwwroot\\*"
                }
            }
        }
    }
}
