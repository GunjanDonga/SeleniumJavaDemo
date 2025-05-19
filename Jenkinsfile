pipeline {
    agent any

    tools {
        jdk 'jdk-22'
        maven 'maven-3.9.9'
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/GunjanDonga/SeleniumJavaDemo.git'
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
                junit '**/target/surefire-reports/*.xml'
            }
        }
    }
}
