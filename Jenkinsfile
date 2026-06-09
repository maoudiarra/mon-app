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
                    apk add --no-cache git

                    cd out

                    touch .nojekyll

                    git init
                    git checkout -B gh-pages

                    git config user.name "Jenkins"
                    git config user.email "jenkins@local"

                    git add .

                    git commit -m "Deploy GitHub Pages" || true

                    git remote add origin https://${GITHUB_USER}:${GITHUB_TOKEN}@github.com/maoudiarra/mon-app.git

                    git push -f origin HEAD:gh-pages
                    '''
                }
            }
        }
    }
}