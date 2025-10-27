pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo 'Cloning source code...'
                git branch: 'main', url: 'https://github.com/hansikagollen/sample-python-project.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                echo 'Installing dependencies...'
                bat 'pip install --upgrade pip'
                bat 'pip install -r requirements.txt'
            }
        }

        stage('Run Tests') {
            steps {
                echo 'Running tests...'
                bat 'pytest .'
            }
        }

        stage('Archive Results') {
            steps {
                echo 'Archiving build artifacts...'
                archiveArtifacts artifacts: '**/*.log', fingerprint: true
            }
        }
    }
}
