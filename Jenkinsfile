pipeline {

    agent any

    

    stages {

        stage('Checkout Code') {

            steps {

                git branch: 'main', url: 'https://github.com/itsmeteja9/Python-docker.git'  // Replace with your repo URL

            }

        }



        stage('Build Docker Image') {

            steps {

                sh 'docker build -t itsmeteja9/python-docker .'  // Replace with your Docker Hub username and image name

            }

        }



        stage('Tag Docker Image') {

            steps {

                bat 'docker tag your-username/your-image:latest your-username/your-image:latest'

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

}
