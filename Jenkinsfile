pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/username/repository.git'
            }
        }
        
        stage('Build') {
            steps {
                script {
                    sh 'npm install'
                    sh 'npm run build'
                }
            }
        }
        
        stage('Test') {
            steps {
                script {
                    sh 'npm test -- --coverage'
                    junit 'coverage/**/*.xml'
                }
            }
        }
        
        stage('Lint') {
            steps {
                script {
                    sh 'npm run lint'
                }
            }
        }
    }

    post {
        always {
            archiveArtifacts artifacts: 'coverage/**', allowEmptyArchive: true
        }
    }
}