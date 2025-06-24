pipeline {
    agent any

    environment {
        APP_PORT = '5000'
    }

    stages {
        stage('Clone Repository') {
            steps {
                git 'https://github.com/USERNAME/flask-ci'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'pip install -r requirements.txt'
            }
        }

        stage('Run Tests') {
            steps {
                sh 'pytest tests'
            }
        }

        stage('Deploy Application') {
            steps {
                sh 'nohup python3 app.py &'
            }
        }
    }
}
