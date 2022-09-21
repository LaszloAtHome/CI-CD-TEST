pipeline{
    agent any
    tools { nodejs 'node' }
    stages {
        stage('build angular app') {
            steps {
                script {
                    bat "npm run ng -- build --configuration=production --output-path dist"
                }
            }
        }
        stage('delete old files') {
            steps {
                script {
                    bat "del /q C:\\inetpub\\wwwroot\\*"
                }
            }
        }
        stage('delete old folders') {
            steps {
                script {
                    bat 'FOR /D %%p IN ("C:\\inetpub\\wwwroot\\*.*") DO rmdir "%%p" /s /q'
                }
            }
        }
        stage('copy new dist') {
          steps {
              script {
                  bat "xcopy .\\dist* c:\\inetpub\\wwwroot\\ /E /d"
              }
          }
        }
        stage('stop iis') {
          steps {
              script {
                  bat "NET STOP IISADMIN"
              }
          }
        }
        stage('start iis') {
          steps {
              script {
                  bat "NET START IISADMIN"
              }
          }
        }
        stage('start w3svc') {
          steps {
              script {
                  bat "NET START W3svc"
              }
          }
        }
    }
}
