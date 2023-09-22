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
                  script 
                    {
                        docker.withRegistry( '', dockerhub-credentials ) {
                            dockerImage.push()
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