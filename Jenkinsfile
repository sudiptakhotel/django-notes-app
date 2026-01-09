pipeline {
    agent { label "rahul" }
    stages{
        stage("Code"){
            steps{
                echo "Cloning repository from github"
                git url: "https://github.com/sudiptakhotel/django-notes-app.git" , branch: "main"
            }
        }
        stage("Build"){
            steps{
                echo "Building Docker image"
                sh "docker build -t notes-app:latest ."
            }
        }
        stage("Push"){
            steps{
                echo "Pushing the image to DockerHub"
                withCredentials([usernamePassword(credentialsId: 'agentDockerHubCred', usernameVariable: 'agentDockerHubUser', passwordVariable: 'agentDockerHubPass')]) {
                    sh "docker login -u ${agentDockerHubUser} -p ${agentDockerHubPass}"
                    sh "docker tag notes-app:latest sudiptakhotel/notes-app:latest"
                    sh "docker push sudiptakhotel/notes-app:latest"
                }
            }
        }
        stage("Deploy"){
            steps{
                echo "Deploying the application"
                sh "docker compose up -d"
            }
        }
    }
}