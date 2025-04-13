pipeline {
    agent any
    stages {
        stage('Checkout SCM') {
            steps {
                checkout scm
            }
        }
        stage('Set up Virtual Environment') {
            steps {
                sh 'python3 -m venv venv' // Create virtual environment
                sh './venv/bin/pip install --upgrade pip' // Upgrade pip
                sh './venv/bin/pip install -r requirements.txt' // Install dependencies
            }
        }
        stage('Run App') {
            steps {
                sh './venv/bin/python app.py' // Run your app
            }
        }
    }
}

