pipeline { 

    environment { 

        registry = "itsmeteja9/java-docker" 

        registryCredential = 'dockerjenkinsintegration' 

        dockerImage = '' 

    }
    agent any 
 

    stage('Build image') {
  
       app = docker.build("itsmeteja9/python-docker")
    }

    stage('Test image') {

        app.inside {
            sh 'echo "Tests passed"'
        }
    }

    stage('Push image') {
        
        docker.withRegistry('https://registry.hub.docker.com', 'docker-hub-credentials') {
            app.push("${env.BUILD_NUMBER}")
        }
    }
    
    stage('Trigger ManifestUpdate') {
                echo "triggering updatemanifestjob"
                build job: 'updatemanifest', parameters: [string(name: 'DOCKERTAG', value: env.BUILD_NUMBER)]
        }
}


        stage('Push Docker Image') {

            steps {

                withCredentials( [  // Use credentials configured in Jenkins

                    username: 'itsmeteja9', 

                    password: 'Applecloud@90' 

                ]) {

                    bat 'docker push your-username/your-image:latest' 

                }

            }

        }

    }


