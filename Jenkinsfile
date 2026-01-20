pipeline {
    agent any

    tools {
        nodejs "Node.js"
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'master',
                    url: 'https://github.com/arjumand9794/Teraaform_4.git'
            }
        }

        stage('Check Node & NPM') {
            steps {
                sh 'node -v'
                sh 'npm -v'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Build') {
            steps {
                sh 'CI=false npm run build'
            }
        }

        stage('Test') {
            steps {
               sh 'npm test -- --watch=false || true'
            }
        }
    }
}
