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

   }

}
