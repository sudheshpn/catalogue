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
                    def dockerfile = 'Dockerfile'
                    def customImage = docker.build("sudheshpn/catalogue:${env.BUILD_ID}", "-f ${dockerfile} ./docker/catalogue") 
                    customImage.push()
                    customImage.push('latest')
                    }
                }
            }
        }
    
}
