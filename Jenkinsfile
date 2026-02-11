pipeline {
    agent {
        docker {
            image 'node:18'
            args '-u root:root'
        }
    }

    environment {
        VERCEL_TOKEN = credentials('devops29-vercel-token')
    }

    stages {

        stage('Check Node') {
            steps {
                sh 'node -v'
                sh 'npm -v'
            }
        }

        stage('Install') {
            steps {
                sh 'npm install'
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
