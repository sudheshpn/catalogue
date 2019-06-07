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
                    def customImage = docker.build("sudheshpn/catalogue:${env.BUILD_NUMBER}","./docker/catalogue/Dockerfile")
                    }
                }
            }
        }
    stage('Push Docker Image') {
       when {
          branch 'master'
       }
       steps {
          script {
                    docker.withRegistry('https://registry.hub.docker.com', 'docker_hub_login') {
                        app.push("${env.BUILD_NUMBER}")
                        app.push("latest")
                    }
                }
            }
        }
}

}
}


