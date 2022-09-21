pipeline{
    agent any

    stages {
        stage('build angular app') {
            steps {
                script {
                    sh "ng build --configuration=production --output-path dist"
                }
            }
        }
        stage('delete old files') {
            steps {
                script {
                    sh "-c 'rm -rf /c/inetpub/wwwroot/*'"
                }
            }
        }
    }
}
