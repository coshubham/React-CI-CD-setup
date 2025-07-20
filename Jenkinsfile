stage('Build') {
    steps {
        bat '''
        dir
        node --version
        npm --version
        npm install
        npm run build
        dir
        '''
    }
}

stage('Test') {
    steps {
        bat '''
        npx vitest
        '''
    }
}
