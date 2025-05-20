pipeline {
    agent any

    tools {
        jdk 'JDK-22'
        maven 'Apache Maven 3.9.9'
    }

    stages {
        stage('Checkout') {
            steps {
               git branch: 'main', url: 'https://github.com/your-username/your-repo.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean install'
            }
        }

        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }

        stage('Publish Results') {
            steps {
                junit '**/surefire-reports/*.xml'
            }
        }
    }
}