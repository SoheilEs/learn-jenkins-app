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
                    ls -la
                    node --version
                    npm --version
                    npm install
                    npm install react-scripts --save
                    npm run build
                    ls -la
                '''
            }
        }
    }
}
