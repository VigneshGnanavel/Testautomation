pipeline {
    agent any

    environment {
        VENV_DIR = 'venv'
    }

    stages {
        stage('Setup') {
            steps {
                bat '''
                echo "Creating virtual environment..."
                pip install virtualenv
                virtualenv %VENV_DIR%
                call %VENV_DIR%\\Scripts\\activate

                echo "Installing dependencies..."
                pip install robotframework
                pip install robotframework-selenium2library
                pip install robotframework-seleniumlibrary
                pip install selenium
                '''
            }
        }

        stage('Run Tests') {
            steps {
                bat '''
                echo "Activating virtual environment..."
                call %VENV_DIR%\\Scripts\\activate

                echo "Running Robot Framework tests..."
                robot path/to/your/tests
                '''
            }
        }
    }

    post {
        always {
            echo 'Archiving test results...'
            archiveArtifacts artifacts: '**/*.xml', allowEmptyArchive: true
            archiveArtifacts artifacts: '**/*.html', allowEmptyArchive: true

            echo 'Cleaning workspace...'
            cleanWs()
        }
    }
}
