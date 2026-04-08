pipeline {
    agent any

    environment {
        TOMCAT_HOME = "C:\\apache-tomcat"  // Change to your Tomcat path
        WAR_FILE = "target\\my-project-1.0-SNAPSHOT.war"
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
                bat """\
                copy /Y "%WORKSPACE%\\${WAR_FILE}" "%TOMCAT_HOME%\\webapps\\my-project.war"
                """
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
