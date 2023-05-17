
pipeline {
  agent any
  
  stages {
  
    stage('Build') {
    
      steps {
        sh 'echo "Building the application..."'
      }
    }
    
    stage('Docker') {
    
      steps {
        
        script{
        def dockerTool = tool name: 'docker-latest-tool', type: 'org.jenkinssci.plugins.docker.commons.tools.DockerTool'
          env.PATH = "${dockerTool}/bin:${env.PATH}"
        }
        
        withCredentials([usernamePassword(credentialsId: 'personal-docker-credentials', usernameVariable: 'DOCKER_USERNAME', passwordVariable: 'DOCKER_PASSWORD')]) {
          sh "echo ${DOCKER_USERNAME}"
        }
        
        
      }
    }
    
  }
}
