pipeline {
    agent { label 'agent1' }   // 👈 THIS is the replacement

    stages {

        stage('Code Checkout') {
            steps {
                git branch: 'master', url: 'https://github.com/Vishal201927/my-project'
            }
        }

        stage('Build') {
            steps {
                bat 'mvn clean package'
            }
        }

        stage('Test') {
            steps {
                bat 'mvn test'
            }
        }

        stage('Deploy') {
            steps {
                bat 'echo Deploying...'
            }
        }
    }
}
