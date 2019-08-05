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
       withSonarQubeEnv(credentialsId: 'sonarcloud') {
       withMaven(jdk: 'java', maven: 'maven') {
       sh 'mvn sonar:sonar  -Dsonar.projectKey=maven-example -Dsonar.organization=imransheik96  -Dsonar.host.url=https://sonarcloud.io -Dsonar.login=dc81cbb61144a6ede85dcd1bcfa3ddfd832103f2' 
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
