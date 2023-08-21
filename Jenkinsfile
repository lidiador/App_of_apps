def frontendImage="wilkmat/frontend_repo"
def backendImage="wilkmat/backend_repo"
def backendDockerTag=""
def frontendDockerTag=""
def dockerRegistry=""
def registryCredentials="Dockerhub"

pipeline {
    agent {
        label 'agent'
    }
    tools {
        terraform 'Terraform'
    }
    stages {
        stage('Get Code') {
            steps {
                checkout scm
            }
        } 
        stage('Clean running containers') {
            steps {
                sh "docker rm -f frontend backend"
            }
        }
        stage('Adjust version') {
            steps {
                script{
                    backendDockerTag = params.backendDockerTag.isEmpty() ? "latest" : params.backendDockerTag
                    frontendDockerTag = params.frontendDockerTag.isEmpty() ? "latest" : params.frontendDockerTag

                    currentBuild.description = "Backend: ${backendDockerTag}, Frontend: ${frontendDockerTag}"
                    }    
                }
}
    }
}