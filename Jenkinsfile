pipeline {
    agent any

    tools {
        maven 'Maven3'   // matches Jenkins Maven installation
        jdk 'Default'    // matches Jenkins JDK installation
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
                sh """
                    mvn sonar:sonar \
                    -Dsonar.projectKey=my-webapp \
                    -Dsonar.host.url=http://16.112.131.238:9000 \
                    -Dsonar.login=squ_70959e6c561736a9fd40c8a21462c3e5300cbd91
                """
            }
        }
    }
}
