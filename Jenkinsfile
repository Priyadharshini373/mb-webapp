pipeline {
    agent any

    tools {
        maven 'Maven3'  // Must match your Maven installation name
    }

    environment {
        SONAR_TOKEN = credentials('sonar-token')  // the token you added in Jenkins Credentials
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
                withSonarQubeEnv('SonarQubeVM2') {  // Name of your SonarQube server in Jenkins
                    sh "sonar-scanner -Dsonar.projectKey=my-webapp -Dsonar.host.url=http://16.112.131.238:9000 -Dsonar.login=$SONAR_TOKEN"
                }
            }
        }
    }
}
