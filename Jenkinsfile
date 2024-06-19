pipeline {
    agent any
    
    environment {
        ROBOT_FRAMEWORK_VERSION = '3.2.1'
        SELENIUM2_LIBRARY_VERSION = '3.0.0'
        SELENIUM_LIBRARY_VERSION = '4.4.0'
        SELENIUM_VERSION = '3.141.0'
        URLLIB3_VERSION = '1.25.9'
    }
    
    stages {
        stage('Install Dependencies') {
            steps {
                script {
                    // Install Python and pip (if necessary)
                    sh 'pip install --upgrade pip setuptools wheel'

                    // Install Robot Framework and Selenium libraries
                    sh "pip install robotframework==${env.ROBOT_FRAMEWORK_VERSION}"
                    sh "pip install robotframework-selenium2library==${env.SELENIUM2_LIBRARY_VERSION}"
                    sh "pip install robotframework-seleniumlibrary==${env.SELENIUM_LIBRARY_VERSION}"
                    sh "pip install selenium==${env.SELENIUM_VERSION}"
                    sh "pip install urllib3==${env.URLLIB3_VERSION}"
                }
            }
        }
        
        stage('Run Tests') {
            steps {
                script {
                    // Execute Robot Framework tests
                    sh 'robot --outputdir results test_cases'
                }
            }
        }
    }
}
