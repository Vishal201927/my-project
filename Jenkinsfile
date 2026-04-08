pipeline {
    agent any

    environment {
        // Correct Tomcat path
        TOMCAT_HOME = "C:\\apache-tomcat-9.0.117-windows-x64"

        // WAR file path after Maven build
        WAR_FILE = "${WORKSPACE}\\target\\my-project-1.0-SNAPSHOT.war"
    }

    stages {

        stage('Code Checkout') {
            steps {
                echo "Checking out code from Git"
                git branch: 'master', url: 'https://github.com/Vishal201927/my-project.git'
            }
        }

        stage('Build') {
            steps {
                echo "Building the project"
                bat 'mvn clean package'
            }
        }

        stage('Test') {
            steps {
                echo "Running tests"
                bat 'mvn test'
            }
        }

        stage('Deploy') {
            steps {
                echo "Deploying WAR to Tomcat"
                // Correct Windows copy command with quotes
                bat "copy /Y \"${WAR_FILE}\" \"${TOMCAT_HOME}\\webapps\\my-project.war\""
            }
        }
    }

    post {
        success {
            echo "Pipeline completed successfully!"
        }
        failure {
            echo "Pipeline failed!"
        }
    }
}
