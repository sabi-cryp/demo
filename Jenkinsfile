pipeline {
    agent any

    stages {
         stage('Clone sources') {
                steps {
                    git url: 'https://github.com/sabi-cryp/demo.git'
                }
            }
         stage("build & SonarQube analysis") {
            agent any
            steps {
              withSonarQubeEnv('My SonarQube Server') {
               sh 'mvn clean verify sonar:sonar  -Dsonar.projectKey=demo   -Dsonar.host.url=http://localhost:9000   -Dsonar.login=1c14ce648c4aa77ffc26ded843f4600811dfc7ef'
                }
            }
          }
    }
}




