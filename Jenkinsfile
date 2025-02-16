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
                sh'''
                        ls -la
                        echo "Checking node and npm versions"
                        node --version
                        npm --version
                        npm ci
                        npm run build
                        ls -la
                    '''
                
            }
        }
    }
}
