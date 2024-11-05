 pipeline {
       agent any

       environment {
           DOCKER_REGISTRY = 'itsmeteja9/python-docker'
           DOCKER_IMAGE = 'python-app'
       }

       stages {
           stage('Build') {
               steps {
                   bat 'docker build -t %DOCKER_REGISTRY%/%DOCKER_IMAGE%:latest .'
               }
           }
           stage('Test') {
               steps {
                   bat 'docker run -t %DOCKER_REGISTRY%/%DOCKER_IMAGE%:latest pytest'
               }
           }
           stage('Push') {
               steps {
                   bat 'docker push %DOCKER_REGISTRY%/%DOCKER_IMAGE%:latest'
               }
           }
           stage('Deploy') {
               steps {
                   bat 'docker run -d -p 80:80 %DOCKER_REGISTRY%/%DOCKER_IMAGE%:latest'
               }
           }
       }
   }
