pipeline {
    agent {label 'docker-vm'}


    stages {
        stage('Git Clone') {
            steps {
               checkout scm
            }
        }
        stage('Build and Push') {
            steps {
                script {
                    def DockerImage = "shivkanshsingh/jenkins-pipeline-app"
                    def DockerTag = "v1.0"
                    def dockerCredentialsId = "dhub_creds"
                    // this is a comment
                    def dockerBuild = docker.build("${DockerImage}:${DockerTag}",".")
                    docker.withRegistry("",dockerCredentialsId) {
                        dockerBuild.push()
                   }
                }
            }
        }

        }



}

