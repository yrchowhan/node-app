pipeline {
    agent any

    environment {
        VERCEL_TOKEN = credentials('vercel-token')   // store your Vercel token in Jenkins credentials
        VERCEL_ORG_ID = credentials('vercel-org-id') // optional: org/project IDs if you want to set them
        VERCEL_PROJECT_ID = credentials('vercel-project-id')
    }

    stages {
        stage('Install') {
            steps {
                sh 'npm install'
            }
        }

        stage('Test') {
            steps {
                sh 'npm test'
            }
        }

        stage('Build') {
            steps {
                sh 'npm run build'
            }
        }

        stage('Deploy to Vercel') {
            steps {
                withEnv(["VERCEL_TOKEN=$VERCEL_TOKEN",
                         "VERCEL_ORG_ID=$VERCEL_ORG_ID",
                         "VERCEL_PROJECT_ID=$VERCEL_PROJECT_ID"]) {
                    sh '''
                        npm install -g vercel
                        vercel --token=$VERCEL_TOKEN --prod --confirm
                    '''
                }
            }
        }
    }
}
