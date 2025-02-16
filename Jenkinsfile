pipeline {
    agent any
    stages {
        stage('Build') {
           agent {
            docker {
                image 'node:18'
                reuseNode false
                }
            }
            steps {
                sh '''
                    echo "Listing files before build"
                    ls -la
                    node --version
                    npm --version
                    echo "Running npm ci"
                    npm ci
                    echo "Running npm run build"
                    npm run build
                    echo "Listing files after build"
                    ls -la
                '''
            }
        }
    }
}
