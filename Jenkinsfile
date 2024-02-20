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
	      				sh 'docker push nanwaribrahim/numeric-app:""$GIT_COMMIT"" .'
	      	      }  
      			}   
      		}
      stage('K8s Deployment - DEV') {
      		steps {
      			  withKubeConfig([credentialsId: 'kubeconfig']) {
      			  sh "sed -i 's#replace#nanwaribrahim/numeric-app:${GIT_COMMIT}#g' k8s_deployment_service.yaml"
      			  sh "kubectl apply -f k8s_deployment_service.yaml"
      			  }
				}
			}
		}
	}			
