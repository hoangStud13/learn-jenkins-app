pipeline {
    agent any

    stages {
        
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

