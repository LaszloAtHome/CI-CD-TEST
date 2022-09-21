pipeline{
    agent any

    stages {
        stage('docker build') {
            steps {
                script {
                    sh "docker build -f CI-CD-TEST/Dockerfile -t laszloathome/CI-CD-TEST:1.0.0-${BUILD_ID}"
                }
            }
        }
        stage('docker push') {
            steps {
                script {
                    sh "docker push laszloathome/CI-CD-TEST:1.0.0-${BUILD_ID}"
                }
            }
        }
        stage('docker compose pull') {
          steps {
              script {
                  sh "docker-compose pull angularapp"
              }
              script {

              }
          }
        }
        stage('docker compose up') {
          steps {
              script {
                  sh "docker-compose up -d angularapp"
              }
          }
        }
    }
}
