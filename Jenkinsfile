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
       post {
           always {
               archiveArtifacts artifacts: 'test-output/**/*.html', fingerprint: true

               publishHTML(target: [
                   reportName: 'Extent Report',
                   reportDir: 'test-output',
                   reportFiles: 'extent-report.html',
                   keepAll: true,
                   alwaysLinkToLastBuild: true,
                   allowMissing: false
               ])
           }
       }


}
