pipeline {
    agent any

    environment {
        VENV_DIR = 'venv'  // Name of virtual environment directory
    }

    stages {
        stage('Clone Repository') {
            steps {
                echo 'Repository is cloned automatically by Jenkins from GitHub.'
            }
        }

        stage('Set Up Python Environment') {
            steps {
                bat '''
                python -m venv %VENV_DIR%
                call %VENV_DIR%\\Scripts\\activate
                pip install --upgrade pip
                pip install -r requirements.txt
                '''
            }
        }

        stage('Run FastAPI App') {
            steps {
                bat '''
                call %VENV_DIR%\\Scripts\\activate
                uvicorn app.main:app --host 0.0.0.0 --port 8000
                '''
            }
        }
    }
}
