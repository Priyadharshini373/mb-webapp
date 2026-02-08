pipeline {
    agent any

    tools {
        maven 'Maven3'              // your Maven installation name in Jenkins
        sonarScanner 'SonarScannerVM2'  // the SonarScanner tool you added
    }

    environment {
        SONAR_TOKEN = credentials('sonar-token')  // the credential ID you created
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
