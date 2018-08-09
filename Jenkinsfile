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

       }         
      stage('Coverage') {

           steps {

               echo 'Coverage..'

            sh './gradlew test jacocoTestReport'

           }

       }   

       stage('CodeQuality') {

           steps {

               echo 'Code Quality..'

            sh './gradlew sonarqube '

           }

       }  
   }

}
