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
                script {
                    // Ensure npm cache is cleared before installing dependencies
                    sh '''
                        echo "Clearing npm cache"
                        npm cache clean --force
                        echo "Checking node and npm versions"
                        node --version
                        npm --version
                        npm ci
                        npm run build
                    '''
                }
            }
        }
    }
}
