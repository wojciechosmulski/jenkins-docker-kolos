pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/wojciechosmulski/jenkins-docker-kolos.git'
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
