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
                sh '''
                    ls -la
                    node --version
                    npm --version
                    npm ci
                    npm run build
                    ls -la
                '''
            }
        }
        stage('without Docker') {
            steps {
                sh '''
                    echo "without docker"
                    touch "without-container.txt"
                '''
            }
        }
       
    }
}