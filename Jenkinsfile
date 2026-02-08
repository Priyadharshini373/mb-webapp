pipeline {
    agent any

    tools {
        maven 'Maven3'              // must match Maven tool name in Jenkins
        sonarRunner 'SonarScannerVM2'  // must match SonarScanner tool name
    }

    environment {
        SONAR_TOKEN = credentials('sonar-token')
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
                sh "sonar-scanner -Dsonar.projectKey=my-webapp -Dsonar.host.url=http://18.60.156.191:9000 -Dsonar.login=$SONAR_TOKEN"
            }
        }
    }
}
