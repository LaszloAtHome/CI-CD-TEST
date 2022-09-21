pipeline{
    agent any

    stages {
        stage('delete old files') {
            steps {
                script {
                    bat "CI/clean.sh"
                }
            }
        }
    }
}
