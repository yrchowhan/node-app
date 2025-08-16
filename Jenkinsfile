pipeline {
    agent any

    environment {
        VERCEL_TOKEN = credentials('vercel-token')
    }
    stages('Install') {
      steps {
        bat 'npm install'
      }
    }
    stages('Test') {
      steps {
        echo 'Skipping tests  -no test scripts found'
      }
    }
    stages('Build') {
      steps {
        bat 'npm run build'
      }
    }
    stages('Deploy') {
      steps {
        bat 'npx vercel --prod --yes --token=%VERCEL_TOKEN%'
      }
    }
}