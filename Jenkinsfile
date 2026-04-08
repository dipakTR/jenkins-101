pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building the application...'
                sh '''
                cd myapp
                # Try to create virtual environment, if it fails use alternative approach
                if ! python3 -m venv venv 2>/dev/null; then
                    echo "Virtual environment creation failed, using --break-system-packages as fallback"
                    pip install --break-system-packages -r requirements.txt
                else
                    echo "Virtual environment created successfully"
                    . venv/bin/activate
                    pip install -r requirements.txt
                fi
                '''
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
                sh '''
                cd myapp
                # Check if virtual environment exists, if so use it
                if [ -d "venv" ]; then
                    . venv/bin/activate
                    python hello.py
                    python hello.py --name=Brad
                else
                    # Use system python if venv wasn't created
                    python3 hello.py
                    python3 hello.py --name=Brad
                fi
                '''
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
