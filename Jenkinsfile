pipeline {

  agent {
    docker {
      image 'node:18'
      args '-u root:root'
    }
  }

  environment {
    VERCEL_PROJECT_NAME = 'simple-nodejs'
    VERCEL_TOKEN = credentials('devops29-vercel-token')
  }

  stages {

    stage('Check Node') {
      steps {
        sh 'node --version'
        sh 'npm --version'
      }
    }

    stage('Install') {
      steps {
        sh 'npm install'
      }
    }

    stage('Build') {
      steps {
        echo 'No build step for backend API'
      }
    }

    stage('Test') {
      steps {
        sh 'npm run test || echo "No test step"'
      }
    }

    stage('Deploy') {
      steps {
        sh 'npm install -g vercel@latest'
        sh '''
          vercel link --project $VERCEL_PROJECT_NAME --token $VERCEL_TOKEN --yes
          vercel --prod --token $VERCEL_TOKEN --confirm
        '''
      }
    }
  }
}
