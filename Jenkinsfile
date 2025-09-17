pipeline {
    agent any

    stages {
        stage('Prepare Directory') {
            steps {
                sh '''
                # Clean old repo inside Jenkins workspace
                rm -rf todo_react_app
                '''
            }
        }

        stage('Checkout SCM') {
            steps {
                checkout scm
            }
        }

        stage('Install & Build') {
            steps {
                dir('todo_react_app') {
                    sh '''
                    npm install
                    CI=false npm run build
                    '''
                }
            }
        }
    }

    post {
        success {
            echo '✅ Build completed successfully!'
        }
        failure {
            echo '❌ Build failed. Check logs.'
        }
    }
}
