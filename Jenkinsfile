pipeline {
    agent any
    triggers { githubPush() }
    stages {
        stage('Checkout') {
            steps { checkout scm }
        }
        stage('Build') {
            steps {
                bat 'python --version'
                bat 'python -m py_compile app.py'
            }
        }
        stage('Test') {
            steps { bat 'python -m unittest test.py' }
        }
    }
    post {
        success { echo 'Build stable' }
        failure { echo 'Build failed' }
    }
}
