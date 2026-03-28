@Library("Shared") _
pipeline {
    agent {label "vinod"}
    triggers {
        githubPush()
    }
    
    stages {
        stage("Hello"){
            steps{
                script{
                    hello()
                }
            }
        }
        stage("code"){
            steps{
                script{
                    clone("https://github.com/jha-aditya67/django-notes-app", "dev")
                }
            }
        }
        stage("Build"){
            steps{
                script{
                    docker_build("notes-app", "latest", "adityajha67")
                }
            }
        }
        stage("Push to DockerHub"){
            steps{
                script{
                    docker_push("notes-app", "latest", "adityajha67")
                }
            }
            }
        stage("Deploy"){
            steps{
                echo "This is deploying the code"
                sh "docker compose  up -d"
            }
        }
    }
}
