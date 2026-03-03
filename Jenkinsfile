pipeline {
    agent any

    tools {
        nodejs 'NodeJS'
    }

    stages {

        stage('Checkout') {
            steps {
                git 'https://github.com/betawins/Trading-UI.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Parallel Build & Audit') {
            parallel {

                stage('Build') {
                    steps {
                        sh 'CI=false npm run build'
                    }
                }

                stage('Security Audit') {
                    steps {
                        sh 'npm audit || true'
                    }
                }
            }
        }

        stage('Archive') {
            steps {
                archiveArtifacts artifacts: 'build/**', fingerprint: true
            }
        }
    }

    post {
        success {
            echo 'Parallel Build Successful'
        }
        failure {
            echo 'Build Failed'
        }
    }
}
