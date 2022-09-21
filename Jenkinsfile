pipeline{
    agent any

    stages {
      stage('npm install') {
            steps {
                script {
                    sh "./install.sh"
                }
            }
        }
        stage('build angular app') {
            steps {
                script {
                    sh "-c 'ng build --configuration=production --output-path dist'"
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
