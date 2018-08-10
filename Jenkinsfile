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
            sh './gradlew test'
           }
       }  

       stage('Coverage') {
           steps {
               echo 'Testing..'
             sh './gradlew test jacocoTestReport'
           }
       } 

       stage('CodeQuality') {
           steps {
               echo 'Testing..'
            sh './gradlew sonarqube'
           }
       }       
   }

    post {
             always {
             junit 'build/test-results/test/*.xml'
             publishHTML (target: [
               allowMissing: false,
               alwaysLinkToLastBuild: false,
               keepAll: true,
               reportDir: 'build/reports/tests/test',
               reportFiles: 'index.html',
               reportName: "Junit Reports"
             	])
             }

             success {
             archiveArtifacts artifacts: 'build/libs/*.war', fingerprint: true
    }
}