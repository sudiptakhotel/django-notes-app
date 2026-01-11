@Library('shared') _

pipeline {
    agent { label "rahul" }
    stages{
        stage("Hello"){
            steps{
                script{
                    hello()
                }
            }
        }
        stage("Code"){
            steps{
                script{
                    clone("https://github.com/sudiptakhotel/django-notes-app.git" , "main")
                }
            }
        }
        stage("Build"){
            steps{
                script{
                    build("sudiptakhotel","notes-app" , "latest")
                }
            }
        }
        stage("Push"){
            steps{
                script{
                    push("sudiptakhotel" , "notes-app" , "latest")
                }
            }
        }
        stage("Deploy"){
            steps{
                script{
                    deploy()
                }
            }
        }
    }
}