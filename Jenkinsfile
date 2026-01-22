@Library("Shared") _

pipeline {
    agent {label "czech"}

    stages {
        stage('Hello') {
            steps {
                script{
                    hello()
                }
            }
        }
        stage('Code') {
            steps {
                script {
                    clone("https://github.com/devarshshah9922-collab/django-notes-app.git", "main")
                }
            }
        }
        stage('Build') {
            steps {
                script{
                    docker_build("notes-app", "latest", "devarshshah9922")
                }
            }
        }
        stage('Test') {
            steps {
                echo 'This is to test the code'
            }
        }
        stage('Push to DockerHub') {
             steps{
                script {
                    docker_push("notes-app", "latest", "devarshshah9922")
                }
             }
        }
        stage('Deploy') {
            steps {
                echo 'This is to deploy the code'
                sh "docker compose up -d"
            }
        }
    }
}
