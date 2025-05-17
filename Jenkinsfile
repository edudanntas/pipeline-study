pipeline {
    agent {
        docker {
            image 'maven:3.9.4-openjdk-17'  // Imagem oficial do Maven com JDK 17
            args '-v /root/.m2:/root/.m2'  // Monta o cache do Maven para acelerar builds
        }
    }
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv('SonarQube') {
                    sh 'mvn sonar:sonar'
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