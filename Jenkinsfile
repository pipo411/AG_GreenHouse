pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh'./gradlew clean assemble'
            }
        }
        stage('Test') {
            steps {
                sh'./gradlew clean test'
            }
        }
        stage('Coverage') {
            steps {
                sh'./gradlew clean jacocoTestReports'
            }
        }
        stage('CodeQuality') {
            steps {
                sh'./gradlew sonarqube'
            }
        }
    }
}