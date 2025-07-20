pipeline {
    agent any
    environment {
        deploy = 'Deploy to Vercel'
        VERCEL_TOKEN = credentials('VERCEL_TOKEN') // Ensure you have a Vercel token stored in Jenkins credentials
    }

    stages {
        stage('Clean Workspace') {
            steps {
                cleanWs()
                checkout scm  // Checkout the source code from the SCM and clean the workspace before building 
            }
        }

        stage('Build') {
            agent {
                docker {
                    image 'node:22.11.0-alpine3.20'
                    args '-u root'
                    reuseNode true
                }
            }
            steps {
                sh '''
                ls -l
                node --version
                npm --version
                npm install
                npm run build
                ls -l
                '''
            }
        }

        stage('Test') {
            agent {
                docker {
                    image 'node:22.11.0-alpine3.20'
                    args '-u root'
                    reuseNode true
                }
            }
            steps {
                sh '''
                npm test
                '''
            }
        }

        stage (deploy) {
            agent {
                docker {
                    image 'node:22.11.0-alpine3.20'
                    args '-u root'
                    reuseNode true
                }
            }
            steps {
                sh '''
                npm install -g vercel
                echo $deploy
                vercel --prod --token=$VERCEL_TOKEN --confirm --name=cicdproject
                '''
            }
            
        }
    }
}
