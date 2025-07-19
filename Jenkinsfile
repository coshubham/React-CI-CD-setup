pipeline {
    agent any

    stages {
        stage('Build') {
            agent {
                docker {
                    image 'node:22.11.0-alpine3.20' // Use a specific Node.js Docker image
                    args '-u root' // Run as root user to avoid permission issues
                    reuseNode true // Reuse the same node for the build
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
        
        }
    }

