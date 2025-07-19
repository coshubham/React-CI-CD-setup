pipeline {
    agent any

    stages {
        stage('Build') {
            agent {
                docker {
                    image 'node:18-alpine' // Use Node.js 18 Alpine image
                    reuseNode true // Reuse the same node for the build
                }
            }
            steps {
              sh '''
              
              ls -l
              node --version
              npm --version
              npm insatll
              npm run build
              ls -l
              
              '''
            }
        }
        
        }
    }

