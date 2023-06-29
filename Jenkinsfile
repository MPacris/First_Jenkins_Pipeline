pipeline {
    agent any


    stages {

        stage('Test') {
            steps {
                script{
                    def nodejsTool = tool name: 'node-20-tool', type: 'jenkins.plugins.nodejs.tools.NodeJSInstallation'
                    env.PATH = "${nodejsTool}/bin:${env.PATH}"

                }
                sh 'node --version'
                sh 'echo "Running tests..."'

            }
        }

        stage('Build') {

            steps {
                sh 'echo "Building the application..."'
            }

        }

        stage('Docker'){

            steps{
                script{
                    def dockerTool = tool name: 'docker-latest-tool', type: 'org.jenkinsci.plugins.docker.commons.tools.DockerTool'
                    env.PATH = "${dockerTool}/bin:${env.PATH}"
                }
                sh 'docker --version'
                sh 'echo "Building image and pushing image to Docker Hub"'
 
            }
        }

        stage('Deploy'){

            steps{
            sh 'echo "Deploying application to EC2 instance..."'
            }

        }

    }

}
