pipeline {
    agent any

   node {
     stage('SCM') {
       git 'https://github.com/sabi-cryp/demo'
     }
     stage('SonarQube analysis') {
       withSonarQubeEnv(credentialsId: 'f225455e-ea59-40fa-8af7-08176e86507a', installationName: 'My SonarQube Server') { // You can override the credential to be used
         //sh 'mvn org.sonarsource.scanner.maven:sonar-maven-plugin:3.7.0.1746:sonar'
         sh 'mvn sonar:sonar   -Dsonar.projectKey=demo   -Dsonar.host.url=http://192.168.1.11:9000   -Dsonar.login=1c14ce648c4aa77ffc26ded843f4600811dfc7ef'
       }
     }
   }

}





//mvn sonar:sonar   -Dsonar.projectKey=demo   -Dsonar.host.url=http://192.168.1.11:9000   -Dsonar.login=1c14ce648c4aa77ffc26ded843f4600811dfc7ef
