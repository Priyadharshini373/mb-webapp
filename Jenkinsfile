pipeline {
    agent any

    tools {
        jdk 'Default'    // matches your JDK in Jenkins
        maven 'Maven'    // matches your Maven in Jenkins
    }

    stages {
        stage('Checkout') {
            steps {
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
