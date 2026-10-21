
pipeline {
    agent any

    options {
        timestamps()
    }

    stages {
        stage('Checkout') {
            steps {
                echo 'Checking out Python Calculator from GitHub'
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo 'Checking Python version'
                bat '"C:\\Users\\tiwar\\AppData\\Local\\Python\\pythoncore-3.14-64\\python.exe" --version'

                echo 'Validating Python syntax'
                bat '"C:\\Users\\tiwar\\AppData\\Local\\Python\\pythoncore-3.14-64\\python.exe" -m py_compile calculator.py test_calculator.py'
            }
        }

        stage('Test') {
            steps {
                echo 'Running automated unit tests'
                bat '"C:\\Users\\tiwar\\AppData\\Local\\Python\\pythoncore-3.14-64\\python.exe" -m unittest -v'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Preparing deployment package'
                bat 'if not exist dist mkdir dist'
                bat 'copy calculator.py dist\\calculator.py'
                echo 'Calculator package prepared successfully'
            }
        }
    }

    post {
        success {
            echo 'Python Calculator CI/CD pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed. Check the Console Output.'
        }
    }
}
