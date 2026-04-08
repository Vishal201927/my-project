pipeline {
    agent any

    environment {
        TOMCAT_HOME = "C:\\apache-tomcat-9.0.117-windows-x64\\apache-tomcat-9.0.117"
        WAR_FILE = "${WORKSPACE}\\target\\myapp.war"
    }

    stages {

        stage('Code Checkout') {
            steps {
                git branch: 'master', url: 'https://github.com/Vishal201927/my-project.git'
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
                bat "copy /Y \"${WAR_FILE}\" \"${TOMCAT_HOME}\\webapps\\myapp.war\""
            }
        }
    }

    post {
        success {
            echo "SUCCESS: Deployed to Tomcat"
        }
        failure {
            echo "FAILED: Check path or build"
        }
    }
}
