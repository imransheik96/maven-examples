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
   
   withSonarQubeEnv() {
    withMaven(jdk: 'java', maven: 'maven') {
    sh 'mvn sonar:sonar -Dsonar.projectKey=maven-example -Dsonar.organization=imransheik96 -Dsonar.host.url=https://sonarcloud.io -Dsonar.login=38fe6003597b3359528701c9bfe21c44999a5537' 
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
    withMaven(jdk: 'JDK-1.8', maven: 'Maven-3.6.1') {
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
