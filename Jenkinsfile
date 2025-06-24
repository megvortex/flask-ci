pipeline {
    agent any

    environment {
        VENV_DIR = 'venv'
	APP_PORT = '5000'
    }

    stages {
        stage('Clone Repository') {
            steps {
                git 'https://github.com/megvortex/flask-ci'
            }
        }

        stage('Setup Python Virtualenv') {
            steps {
                sh '''
                    python3 -m venv $VENV_DIR
                    . $VENV_DIR/bin/activate
                    pip install --upgrade pip
                    pip install -r requirements.txt
                '''
            }
        }

        stage('Run Tests') {
            steps {
                sh '''
                    . $VENV_DIR/bin/activate
                    pytest tests
                '''
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                    . $VENV_DIR/bin/activate
                    nohup python app.py &
                '''
            }
        }
    }
}
