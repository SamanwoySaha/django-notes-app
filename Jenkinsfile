@Library("Shared") _
pipeline {
    agent {label "vinod"}
    stages {
        stage("hello") {
            steps {
                script {
                    hello()
                }
            }
        }
        stage("Code") {
            steps{
                script{
                    git_clone("https://github.com/SamanwoySaha/django-notes-app.git", "dev")
                }
            }
        }
        stage("build") {
            steps {
                script{
                    docker_build("samanwoysaha", "notes-app", "latest")
                }
            }
        }
        stage("push to dockerHub") {
            steps {
                script{
                    docker_push("samanwoysaha", "notes-app", "latest")
                }
            }
        }
        stage("deploy") {
            steps {
                script{
                    docker_compose()
                }
            }
        }
    }
}
