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
