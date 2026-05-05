pipeline {
    agent any

    stages {
        stage('Build with Docker') {
            steps {
                sh 'docker run --rm -v $PWD:/app -w /app node:20-alpine npm install'
                sh 'docker run --rm -v $PWD:/app -w /app node:20-alpine npm run build'
            }
        }
    }
}