
pipeline {
  agent any
  
  stages {
    
    stage('Test') {
      
      steps {
        script {
          def nodejsTool = tool name: 'node-19-tool', type: 'jenkins.plugins.nodejs.tools.NodeJSInstallation'
            env.PATH = "${nodejsTool}/bin:${env.PATH}" 
        }
        sh 'echo "Running tests..."' 
        sh 'node --version'
      }
    }
  
    stage('Build') {
    
      steps {
        sh 'echo "Building the application..."'
      }
    }
    
    stage('Docker') {
    
      steps {
        
        script {
          def dockerTool = tool name: 'docker-latest-tool', type: 'org.jenkinsci.plugins.docker.commons.tools.DockerTool'
            env.PATH = "${dockerTool}/bin:${env.PATH}"
        }
        
        withCredentials([usernamePassword(credentialsId: 'personal-docker-credentials', usernameVariable: 'DOCKER_USERNAME', passwordVariable: 'DOCKER_PASSWORD')]) 
        {
          sh "echo ${DOCKER_USERNAME}"
          sh 'docker - - version'
        }
        
        
      }
    }
    
    stage('Deploy') {
      steps {
      sh 'echo "Deploying application to EC2 instance…"'
      }
    }
    
  }
}
