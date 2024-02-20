pipeline {
  agent any

  stages {
      stage('Build Artifact') {
            steps {
              sh "mvn clean package -DskipTests=true" #test123
              archive 'target/*.jar'
            }
        }   
    }
}
