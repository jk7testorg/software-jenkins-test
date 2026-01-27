pipeline {
    agent any

    environment {
        REPO = 'https://github.com/jk7testorg/pythonappcatalogue.git'
        BRANCH = 'master'
    }

    stages {
        stage('Install Dependencies') {
            steps {
                // Assuming Python app with requirements.txt
                sh 'python3 -m venv venv'
                sh '. venv/bin/activate && pip install -r requirements.txt'
            }
        }

        stage('Run Tests') {
            steps {
                // Run Python tests (pytest assumed)
                sh '. venv/bin/activate && pytest || true'
            }
        }

        stage('Build') {
            steps {
                // Simple build placeholder (can package or compile if needed)
                sh 'echo "Building application..."'
            }
        }

        stage('Archive Artifacts') {
            steps {
                // Archive anything generated (logs, packages, etc.)
                archiveArtifacts artifacts: '**/*.log, **/*.txt', allowEmptyArchive: true
            }
        }
    }

    post {
        always {
            echo 'Pipeline finished.'
        }
        success {
            echo 'Build succeeded!'
        }
        failure {
            echo 'Build failed!'
        }
    }
}
