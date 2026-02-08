pipeline {
    agent any

    tools {
        maven 'Maven3'  // Name of Maven installation in Jenkins
        jdk 'Default'    // Make sure Java17 is installed in Jenkins
    }

    environment {
        SONAR_TOKEN = credentials('sonar-token') // Jenkins credentials ID for SonarQube token
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/Priyadharshini373/mb-webapp.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('SonarQube Analysis') {
            steps {
                dir('') {  // Root of the project, where pom.xml exists
                    withSonarQubeEnv('SonarQubeVM2') {
                        sh """
                        mvn sonar:sonar \
                        -Dsonar.projectKey=my-webapp \
                        -Dsonar.host.url=http://16.112.131.238:9000 \
                        -Dsonar.login=$SONAR_TOKEN
                        """
                    }
                }
            }
        }
    }
}
