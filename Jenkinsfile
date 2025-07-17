pipeline {
    agent any

    tools {
        maven 'Maven 3.8.8'
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/arjunpilakkal/simple-java/.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }

        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv('MySonarQube') {
                    sh 'mvn sonar:sonar'
                }
            }
        }
    }
}
