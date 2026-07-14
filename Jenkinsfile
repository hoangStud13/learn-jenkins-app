pipeline {
    agent any

    stages {
        
        stage('Build') {
            agent{
                docker {
                    image 'node:18-alpine'
                    reuseNode true
                    }
                }
            steps {
                sh'''

                npm ci
                npm run build
                ls -la

                '''
            }
                
            }

            stage('Test') {
            agent{
                docker {
                    image 'node:18-alpine'
                    reuseNode true
                    }
                }
            steps {
                sh'''
                echo check if build exists

                test -f build/index.html && echo build exists

                npm test

                '''
            }
                
            }

            

        }

        post{
              always {
                junit 'test-results/junit.xml'
              }
            }
    }

