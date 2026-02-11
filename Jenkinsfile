pipeline {
    agent any

    environment {
        VERCEL_TOKEN = credentials('devops29-vercel-token')
    }

    stages {

        stage('Test npm') {
            steps {
                sh 'node -v'
                sh 'npm -v'
            }
        }

        stage('Build') {
            steps {
                sh 'npm ci'
                sh 'npm run build || echo "No build step"'
            }
        }

        stage('Test Build') {
            steps {
                sh 'npm run test || echo "No test step"'
            }
        }

        stage('Deploy') {
            steps {
                sh 'npm install -g vercel'
                sh 'vercel --token=$VERCEL_TOKEN --prod --confirm'
            }
        }
    }
}
