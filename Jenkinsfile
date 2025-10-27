pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo 'Cloning source code...'
                git 'https://github.com/hansikagollen/sample-python-project.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                echo 'Installing dependencies...'
                sh 'pip install --upgrade pip'
                sh 'pip install -r requirements.txt'
            }
        }

        stage('Run Tests') {
            steps {
                echo 'Running unit tests...'
                sh 'pytest .'
            }
        }

        stage('Archive Results') {
            steps {
                echo 'Archiving Python scripts...'
                archiveArtifacts artifacts: '**/*.py', fingerprint: true
            }
        }
    }
}
