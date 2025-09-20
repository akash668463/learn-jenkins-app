pipeline {
    agent any

    stages {
        stage('Build') {
            agent{
                docker{
                    image 'node:18-alpine'
                    reuseNode true
                }
            }
            steps {
               sh'''
                    ls -la
                    node --version
                    npm --version
                    npm ci
                    npm run build
                    ls -ls
               '''
            }
        }
        stage('Test') {
            agent{
                docker{
                    image 'node:18-alpine'
                    reuseNode true
                }
            }
            steps {
               sh'''
                    echo 'Test stage'
                    npm test
               '''
            }
        }   
    }
}
