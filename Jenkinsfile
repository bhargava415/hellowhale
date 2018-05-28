pipeline {
  agent any
  stages {
     stage('Docker Build') {
      agent any
      steps {
        sh 'docker build -t bhargava1/devops:hellowhale .'
      }
    }
    stage('Docker Push') {
      agent any
      steps {
        withCredentials([usernamePassword(credentialsId: 'dockerHub', passwordVariable: 'dockerHubPassword', usernameVariable: 'dockerHubUser')]) {
          sh "docker login -u ${env.dockerHubUser} -p ${env.dockerHubPassword}"
          sh 'docker push bhargava1/devops:hellowhale'
        }
      }
   }
 }
}