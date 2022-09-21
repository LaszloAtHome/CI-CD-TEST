pipeline{
    agent any
    tools { nodejs 'node' }
    stages {
        stage('stop IIS') {
          steps {
              script {
                  bat "iisreset /stop"
              }
          }
        }
        stage('build angular app') {
            steps {
                script {
                    bat "npm run ng -- build --configuration=production --output-path dist"
                }
            }
        }
        stage('delete old folders & files') {
            steps {
                script {
                    bat "del /q C:\\inetpub\\wwwroot\\*"
                    bat 'FOR /D %%p IN ("C:\\inetpub\\wwwroot\\*.*") DO rmdir "%%p" /s /q'
                    bat 'mkdir C:\\inetpub\\wwwroot\\api'
                }
            }
        }
        stage('copy new dist') {
          steps {
              script {
                  bat "xcopy .\\dist\\* c:\\inetpub\\wwwroot\\ /E /d"
              }
          }
        }
        stage('start IIS') {
          steps {
              script {
                  bat "iisreset /start"
              }
          }
        }
    }
}
