pipeline {

   agent any

   stages {

       stage('Build') {

           steps {

               echo 'Building..'

            sh './gradlew clean assemble'

           }

       }

    
   }


}