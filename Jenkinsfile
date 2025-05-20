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
               // Run tests but never fail the build here
               catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE') {
                   sh 'mvn clean install'
               }
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