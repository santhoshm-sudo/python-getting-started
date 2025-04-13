pipeline {
    agent any

    environment {
        VENV = 'venv'
    }

    stages {
        stage('Checkout SCM') {
            steps {
                checkout scm
            }
        }

        stage('Set up Virtual Environment') {
            steps {
                sh 'python3 -m venv $VENV'
                sh './$VENV/bin/pip install --upgrade pip'
                sh './$VENV/bin/pip install -r requirements.txt'
            }
        }

        stage('Run Migrations') {
            steps {
                sh './$VENV/bin/python manage.py migrate'
            }
        }

        stage('Run Server') {
            steps {
                sh './$VENV/bin/python manage.py runserver 0.0.0.0:8000 &'
            }
        }
    }
}

