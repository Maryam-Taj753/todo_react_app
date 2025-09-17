pipeline {
    agent any

    stages {
        stage('Prepare Directory') {
            steps {
                sh '''
                mkdir -p /home/ubuntu/maryam
                cd /home/ubuntu/maryam

                # Remove old repo to avoid "already exists" error
                rm -rf todo_react_app
                '''
            }
        }

        stage('Clone Repository') {
            steps {
                dir('/home/ubuntu/maryam') {
                    sh 'git clone https://github.com/Maryam-Taj753/todo_react_app.git'
                }
            }
        }

        stage('Install & Build') {
            steps {
                dir('/home/ubuntu/maryam/todo_react_app') {
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
