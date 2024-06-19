pipeline {
    agent any

    stages {
        stage('Install Dependencies') {
            steps {
                bat 'pip install --upgrade pip setuptools wheel'
                bat "pip install robotframework==${env.ROBOT_FRAMEWORK_VERSION}"
                bat "pip install robotframework-selenium2library==${env.SELENIUM2_LIBRARY_VERSION}"
                bat "pip install robotframework-seleniumlibrary==${env.SELENIUM_LIBRARY_VERSION}"
                bat "pip install selenium==${env.SELENIUM_VERSION}"
                bat "pip install urllib3==${env.URLLIB3_VERSION}"
            }
        }

        stage('Run Tests') {
            steps {
                bat 'robot --outputdir results test_cases'
            }
        }
    }
}
