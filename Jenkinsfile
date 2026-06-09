pipeline {
    agent any

    environment {
        GITHUB_USERNAME = 'maoudiarra'
    }

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

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

        stage('Export HTML Static') {
            steps {
                sh 'ls -la out'
            }
        }

        stage('Deploy GitHub Pages') {
            steps {
                withCredentials([
                    usernamePassword(
                        credentialsId: 'github-token',
                        usernameVariable: 'GITHUB_USER',
                        passwordVariable: 'GITHUB_TOKEN'
                    )
                ]) {

                    sh '''
                    cd out

                    touch .nojekyll

                    git init
                    git checkout -B gh-pages

                    git config user.email "jenkins@local"
                    git config user.name "Jenkins"

                    git add .
                    git commit -m "Deploy from Jenkins" || true

                    git remote add origin https://${GITHUB_USER}:${GITHUB_TOKEN}@github.com/maoudiarra/mon-app.git

                    git push -f origin HEAD:gh-pages
                    '''
                }
            }
        }
    }

    post {
        success {
            echo 'Déploiement terminé'
        }

        failure {
            echo 'Pipeline en erreur'
        }
    }
}