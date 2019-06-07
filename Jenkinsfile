pipeline {
      environment {
      registry = "sudheshpn/catalogue"
      registryCredential = 'docker_hub_login'
  }
    agent any
    stages {
        stage('Build Docker Image') {
            when {
                branch 'master'
            }
            steps {
                script {
                    docker.build -t registry + ":$BUILD_NUMBER" -f docker/catalogue/Dockerfile .
                    }
                }
            }
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


