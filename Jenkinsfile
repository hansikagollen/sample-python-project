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
                bat 'python -m pip install --upgrade pip'
                bat 'pip install -r requirements.txt'
            }
        }

        stage('Verify Files') {
            steps {
                echo 'Listing files in workspace...'
                bat 'dir'
            }
        }

        stage('Run Tests') {
            steps {
                echo 'Running tests...'
                bat 'pytest --maxfail=1 --disable-warnings -q --junitxml=report.xml'
            }
        }

        stage('Archive Results') {
            steps {
                echo 'Archiving build artifacts and test results...'
                // Archive test report XML file instead of .log
                archiveArtifacts artifacts: '**/report.xml', fingerprint: true, allowEmptyArchive: true
                // Publish test results to Jenkins dashboard
                junit 'report.xml'
            }
        }
    }
}
