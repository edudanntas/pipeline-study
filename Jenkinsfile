pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Build') {
            steps {
                sh './mvnw clean package'
            }
        }
        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv('SonarQube') {
                    sh "./mvnw sonar:sonar -Dsonar.projectKey=teste-pipe -Dsonar.projectName='teste-pipe'"
                }
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploy realizado com sucesso!'
            }
        }
    }
}