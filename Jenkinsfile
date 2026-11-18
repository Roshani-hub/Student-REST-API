
pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                echo 'Retrieving source code from GitHub'
                checkout scm
            }
        }

        stage('Install Dependencies') {
            steps {
                echo 'Installing dependencies'
                sh 'npm install'
            }
        }

        stage('Test') {
            steps {
                echo 'Testing the REST API application'
                sh 'npm test'
            }
        }

        stage('Build') {
            steps {
                echo 'Building the application'
                sh 'npm run build'
            }
        }

        stage('Archive Artifacts') {
            steps {
                echo 'Archiving generated artifacts'
                archiveArtifacts artifacts: 'dist/**',
                                 fingerprint: true
            }
        }
    }

    post {
        success {
            echo 'Pipeline executed successfully!'
        }

        failure {
            echo 'Pipeline execution failed!'
        }
    }
}
