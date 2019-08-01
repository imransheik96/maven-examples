node {
   
   stage('Code Checkout') { 
     git credentialsId: 'githubID', url: 'https://github.com/imransheik96/maven-examples.git'
     
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
   
   withSonarQubeEnv(credentialsId: 'sonarid') {
    withMaven(jdk: 'java', maven: 'maven') {
    sh 'mvn sonar:sonar' 
      }
    }
  stage("Quality Gate"){
          timeout(time: 1, unit: 'HOURS') {
              def qg = waitForQualityGate()
              if (qg.status != 'OK') {
                  error "Pipeline aborted due to quality gate failure: ${qg.status}"
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
