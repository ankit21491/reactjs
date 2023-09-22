pipeline{
  environment {
    registry = "ankit21sh/ankit"
    registryCredential = 'dockerhub'
    dockerImage = ''
  }
  agent any
    stages {
        stage('Building image') {
            steps{
                script {
                  dockerImage = docker.build registry + ":latest"
                }
             }
          }
          stage('Push Image') {
              steps{
                  withCredentials([usernamePassword(credentialsId: 'dockerhub-credentials', passwordVariable: 'dockerpsd', usernameVariable: 'dockerusr')]) {
    
	                  script{
                      bat """
                        echo "${dockerpsd}" | docker login --username ${dockerusr} --password-stdin
                        docker push ankit21sh/ankit:latest
                      """
                      
                    }
                  }
               }
            }
//         stage('Deploying into k8s'){
//             steps{
//                 sh 'kubectl apply -f deployment.yml'
//             }
//         }
     }
 }