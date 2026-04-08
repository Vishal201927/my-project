pipeline {
    agent any

    environment {
        // Path to your Tomcat installation
        TOMCAT_HOME = "C:\\apache-tomcat"  
        // Path to the WAR file Maven produces
        WAR_FILE = "target/my-project-1.0-SNAPSHOT.war"
        // Git repository
        GIT_URL = "https://github.com/Vishal201927/my-project.git"
        GIT_BRANCH = "master"
    }

    stages {

        stage('Code Checkout') {
            steps {
                echo "Checking out code from Git"
                git branch: "${env.GIT_BRANCH}", url: "${env.GIT_URL}"
            }
        }

        stage('Build') {
            steps {
                echo "Building the project with Maven"
                bat 'mvn clean package'
            }
        }

        stage('Test') {
            steps {
                echo "Running Maven tests"
                bat 'mvn test'
            }
        }

        stage('Deploy') {
            steps {
                echo "Deploying WAR to Tomcat"
                // Stop Tomcat (optional)
                bat "taskkill /F /IM java.exe || exit 0" 
                // Copy WAR to webapps folder
                bat "copy /Y ${env.WAR_FILE} ${env.TOMCAT_HOME}\\webapps\\"
                // Start Tomcat
                bat "${env.TOMCAT_HOME}\\bin\\startup.bat"
                echo "WAR deployed and Tomcat started"
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
