pipeline {
    agent { label 'agent1' }   // 🔑 MOST IMPORTANT LINE

    stages {
        stage('Code Checkout') {
            steps {
                echo 'Checking out code...'
            }
        }

        stage('Build') {
            steps {
                echo 'Building project...'
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying application...'
            }
        }
    }
}
