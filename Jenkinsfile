pipeline {
    agent any

    tools {
        jdk 'Java17'   // Make sure you have JDK17 configured in Jenkins
        maven 'Maven3' // Make sure Maven3 is configured
    }

    environment {
        SONAR_TOKEN = credentials('sonar-token')
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/Priyadharshini373/mb-webapp.git'
            }
        }

        stage('Build & Test') {
            steps {
                sh 'mvn clean test package'
            }
        }

        stage('SonarQube Analysis') {
            steps {
                sh """
                    mvn sonar:sonar \
                    -Dsonar.projectKey=my-webapp \
                    -Dsonar.host.url=http://16.112.131.238:9000 \
                    -Dsonar.login=squ_f28140a0895709a57c0b058884e1079413eb0f09
                """
            }
        }
    }
}
