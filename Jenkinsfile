pipeline{
    agent any
    tools {
        nodejs: '16.15.1'
    }
    stages {
        stage('build angular app') {
            steps {
                script {
                    bat "npm run ng build --configuration=production --output-path dist"
                }
            }
        }
        stage('delete old files') {
            steps {
                script {
                    bat "rmdir /S /Q C:\\inetpub\\wwwroot && mkdir C:\\inetpub\\wwwroot"
                }
            }
        }
        stage('copy new dist') {
          steps {
              script {
                  sh "xcopy .\\dist c:\\inetpub\\wwwroot\\"
              }
          }
        }
        stage('stop iis') {
          steps {
              script {
                  sh "NET STOP IISADMIN"
              }
          }
        }
        stage('start iis') {
          steps {
              script {
                  sh "NET START IISADMIN"
              }
          }
        }
        stage('start w3svc') {
          steps {
              script {
                  sh "NET START W3svc"
              }
          }
        }
    }
}
