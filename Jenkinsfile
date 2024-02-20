pipeline {
  agent any

  stages {
      stage('Build Artifact') {
            steps {
              sh "mvn clean package -DskipTests=true"
              archive 'target/*.jar' //testcomment123
            }
        }
      stage('Unit Tests') {
            steps {
              sh "mvn test"
            }
        }         
    }
}
