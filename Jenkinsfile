pipeline {
    agent any

    tools {
        jdk 'JDK-22'
        maven 'Apache Maven 3.9.9'
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/GunjanDonga/SeleniumJavaDemo.git'
            }
        }

        stage('Build') {
            steps {
                // Only build, do NOT run tests
                sh 'mvn clean install -DskipTests'
            }
        }

        stage('Test') {
            steps {
                // Run tests separately
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
