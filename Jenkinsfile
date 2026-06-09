pipeline {
    agent {
        docker {
            image 'node:20-alpine'
        }
    }

    stages {

        stage('Install') {
            steps {
                sh 'npm ci'
            }
        }

        stage('Build') {
            steps {
                sh 'npm run build'
            }
        }

        stage('Export') {
            steps {
                sh 'ls -la out'
            }
        }
    }
}