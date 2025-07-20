pipeline {
    agent any

    stages {
        stage('Clean Workspace') {
            steps {
                cleanWs()
                checkout scm  // Checkout the source code from the SCM and clean the workspace before building 
            }
        }

        stage('Build') {
            // agent {
            //     docker {
            //         image 'node:22.11.0-alpine3.20'
            //         args '-u root'
            //         reuseNode true
            //     }
            // }
            steps {
                bat '''
                dir
                node --version
                npm --version
                npm install
                npm ci
                npx vite --version
                dir
                '''
            }
        }

        stage('Test') {
            // agent {
            //     docker {
            //         image 'node:22.11.0-alpine3.20'
            //         args '-u root'
            //         reuseNode true
            //     }
            // }
            steps {
                bat '''
                 npx vitest run            
                 '''
            }
        }
    }
}
