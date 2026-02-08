pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/Priyadharshini373/mb-webapp.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }
    }
}
