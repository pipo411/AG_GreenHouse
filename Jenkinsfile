pipeline {
   agent any
   stages {

       stage('Build') {
           steps {
               echo 'Building..'
            sh './gradlew clean assemble'
           }
           post{
               success {
                archiveArtifacts artifacts: 'build/libs/*.war', fingerprint: true
              }   
           }
       }

       stage('Test') {
           steps {
               echo 'Testing..'
            sh './gradlew test'
           }
           post{
               publishHTML (target: [
             allowMissing: false,
             alwaysLinkToLastBuild: false,
             keepAll: true,
             reportDir: 'build/reports/tests/test',
             reportFiles: 'index.html',
             reportName: "Test Summary"
	       ])  
           }
       }
  
       stage('Coverage') {
           steps {
               echo 'Coverage..'
             sh './gradlew test jacocoTestReport check'
           }
           post{
            publishHTML (target: [
             allowMissing: false,
             alwaysLinkToLastBuild: false,
             keepAll: true,
             reportDir: 'build/reports/findbugs',
             reportFiles: 'main.html',
             reportName: "FindBugs Test"
	       ])
           publishHTML (target: [
             allowMissing: false,
             alwaysLinkToLastBuild: false,
             keepAll: true,
             reportDir: 'build/reports/findbugs',
             reportFiles: 'test.html',
             reportName: "FindBugs Test"
	       ])
           publishHTML (target: [
             allowMissing: false,
             alwaysLinkToLastBuild: false,
             keepAll: true,
             reportDir: 'build/reports/pmd',
             reportFiles: 'main.html',
             reportName: "PMD Test"
	       ])
           publishHTML (target: [
             allowMissing: false,
             alwaysLinkToLastBuild: false,
             keepAll: true,
             reportDir: 'build/reports/pmd',
             reportFiles: 'test.html',
             reportName: "PMD Test"
	       ])
           }
       } 

        stage('Package') {
           steps {
               echo 'CodeQuality..'
            sh './gradlew clean war'
           }
           post{
               success {
                archiveArtifacts artifacts: 'build/libs/*.war', fingerprint: true
              }   
           }
       }

       stage('CodeQuality') {
           steps {
               echo 'CodeQuality..'
            sh './gradlew clean sonarqube'
           }
           
       }       
   }
}
