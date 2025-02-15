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
                        echo "Installing dependencies with npm install"
                        npm install 
                        echo "Building project"
                        npm run build || { echo "Build failed"; exit 1; }
                    '''
                }
            }
        }
    }
}
