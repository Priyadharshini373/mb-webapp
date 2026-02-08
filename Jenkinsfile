pipeline {
    agent any

    tools {
        // Use the JDK and Maven configured in Jenkins
        jdk 'Default'
        maven 'Default'
    }

    stages {
        stage('Checkout') {
            steps {
                // Replace with your GitHub repo URL
                git branch: 'main', url: 'https://github.com/Priyadharshini373/mb-webapp.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean install'
            }
        }

        stage('Run') {
            steps {
                // Optional: run the app to check it's working
                sh 'mvn spring-boot:run &'
            }
        }
    }

    post {
        success {
            echo 'Build and pipeline successful!'
        }
        failure {
            echo 'Pipeline failed!'
        }
    }
}
