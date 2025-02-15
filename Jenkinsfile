pipeline {
    agent any

    stages {
        stage('Build') {
            agent {
                docker {
                    image 'node:18-alpine'
                    reuseNode true
                }
            }
            steps {
                sh '''
                    echo "Clearing npm cache"
                    npm cache clean --force
                    echo "Checking node and npm versions"
                    node --version
                    npm --version
                    echo "Installing dependencies with npm ci"
                    npm ci || cat /home/node/.npm/_logs/*.log
                    echo "Building project"
                    npm run build
                '''
            }
        }
    }
}
