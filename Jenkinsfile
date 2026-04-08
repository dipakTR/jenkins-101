pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building the application...'
                sh '''
                cd myapp
                pip install -r requirements.txt
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
                sh '''
                cd myapp
                python3 hello.py
                python3 hello.py --name=Brad
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying the application...'
                // Add deployment steps here, such as deploying to a server
                // sh 'make deploy'
            }
        }
    }
}
