pipeline {

   agent any

   stages {

       stage('Build') {

           steps {

               echo 'Building..'

            sh './gradlew clean assemble'

           }

       }

       stage('Test') {

           steps {

               echo 'Testing..'

            sh './gradlew test jacocoTestReport'

           }

       }        stage('Code quality analysis...') {

           steps {

               echo 'sonarqube...'

            sh './gradlew sonarqube '

           }

       }    

   }

}