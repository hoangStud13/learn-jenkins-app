pipeline {
    agent any

    stages {

        stage("Checkout"){

          steps{

            echo "Cloning repo"
            git branch: 'main', 
                url:'https://github.com/hoangStud13/learn-jenkins-app.git'

          }

        }
        
        stage('Install') {
            agent{
                docker {
                    image 'node:18-alpine'
                    reuseNode true
                    }
                }
            steps {
                sh'''

                npm install
                npm build

                '''
            }
                
            }

            stage('with docker') {
              steps{
                sh '''
                npm start
                '''
              }
            }
            
        }
    }

