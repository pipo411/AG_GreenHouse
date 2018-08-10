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

           publishHTML (target: [
             allowMissing: false,
             alwaysLinkToLastBuild: false,
             keepAll: true,
             reportDir: 'build/reports/tests/test',
             reportFiles: 'index.html',
             reportName: "Test Summary"
	       ])
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
       success {
           archiveArtifacts artifacts: 'build/libs/*.jar', fingerprint: true
       }      
    }	
}