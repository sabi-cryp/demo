pipeline {
        agent none
        stages {
          stage("build & SonarQube analysis") {
            agent any
            steps {
              withSonarQubeEnv('My SonarQube Server') {
               sh '''
                   mvn org.sonarsource.scanner.maven:sonar-maven-plugin:3.9.1.2184:sonar\
                   -Dsonar.projectKey=demo\
                   -Dsonar.login=1c14ce648c4aa77ffc26ded843f4600811dfc7ef\
                   -Dsonar.host.url=http://localhost:9000\
                   -Dsonar.projectName=${SONAR_PROJECT_NAME} \
                   -Dsonar.java.coveragePlugin=jacoco \
                   -Dsonar.jacoco.reportPaths=target/jacoco.exec \
                   -Dsonar.junit.reportsPaths=target/surefire-reports
                   '''
              }
            }
          }
          stage("Quality Gate") {
            steps {
              timeout(time: 1, unit: 'HOURS') {
                waitForQualityGate abortPipeline: true
              }
            }
          }
        }
      }







