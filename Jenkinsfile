pipeline {
      agent any
      environment {
      registry = "sudheshpn/catalogue"
      registryCredential = 'docker_hub_login'
  }
    
    stages {
        stage('Build Docker Image') {
            when {
                branch 'master'
            }
            steps {
                script {
                    checkout scm  
                    def customImage = docker.build("sudheshpn/catalogue:${env.BUILD_ID}", "-f ./docker/catalogue/Dockerfile .") 
                    customImage.push()
                    customImage.push('latest')
                    }
                }
            }
        }
    
}
