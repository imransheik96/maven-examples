node {
   
   stage('Code Checkout') { 
     git credentialsId: 'github', url: 'https://github.com/imransheik96/maven-examples.git'
     
    }
   stage('Build') {
    withMaven(jdk: 'java', maven: 'maven') {
      sh 'mvn clean compile'
      }
    }
   stage('Unit Test run') {
    withMaven(jdk: 'java', maven: 'maven') {
     sh 'mvn test'
      } 
    }
     
stage('Sonarqube analysis'){
      def scannerHome = tool 'javascanner';
   withSonarQubeEnv(credentialsId: 'sonarcloud') {
    withMaven(jdk: 'java', maven: 'maven') {
    sh 'mvn sonar:sonar' 
      }
    }
}
   stage('Package to Jfrog') {
    withMaven(jdk: 'java', maven: 'maven') {
     sh 'mvn package'
      }
    }
   
   stage('Deploy to Dev') {
     
    }
   stage('Automation Testing') {
     
    }
   stage('Deploy to Test') {
     
    }
   stage('Smoke Testing') {
     
    }
   stage('Deploy to Prod') {
     
    }
   stage('Acceptance Testing') {
     
    }
}
