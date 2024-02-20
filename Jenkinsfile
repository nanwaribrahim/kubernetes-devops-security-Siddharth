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
      stage('Docker Build and Push') {
      		steps {
      		  sh 'printenv'
      		  sh 'docker build -t nanwaribrahim/numeric-app:""$GIT_COMMIT"".'
      		  sh 'docker push nanwaribrahim/numeric-app:""$GIT_COMMIT""'
      		}   
      	}	
    }
}
