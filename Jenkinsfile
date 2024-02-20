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
      		  	withDockerRegisty([credentialsId: “docker-hub”, url: “”]) {
					sh 'printenv'
	      		    sh 'docker build -t nanwaribrahim/numeric-app:""$GIT_COMMIT"" .'
	      		    sh 'docker push nanwaribrahim/numeric-app:""$GIT_COMMIT""'
	      		  }  
      			}   
      		}	
      }
}
