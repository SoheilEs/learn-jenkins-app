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
                        echo "Checking node and npm versions"
                        node --version
                        npm --version
                        npm run build
                    '''
                }
            }
        }
    }
}
