pipeline {
    agent any
    stages{
        stage("Clone Code"){
            steps{
                git url: "https://github.com/vineetkhisty/TO-DO.git", branch: "master"
            }
        }
        stage("Build and Test"){
            steps{
             app = bat "docker build . -t node-app-test-new"
            }
        }
        stage("Push to Image to ECR"){
            steps{
//                 withCredentials([usernamePassword(credentialsId:"193bfa88-a70d-4319-96a5-b1a13b098adf",passwordVariable:"devopsengineeranshu1234$",usernameVariable:"anshude1056@gmail.com")]){
//                 bat "docker tag node-app-test-new ${env.dockerHubUser}/node-app-test-new:latest"
//                 bat "docker login -u ${env.dockerHubUser} -p ${env.dockerHubPass}"
//                 bat "docker push ${env.dockerHubUser}/node-app-test-new:latest"
                 docker.withRegistry('https://434433864791.dkr.ecr.us-east-1.amazonaws.com', 'ecr:us-east-1:193bfa88-a70d-4319-96a5-b1a13b098adf') {
                  app.push("${env.BUILD_NUMBER}")
                  app.push("latest")
                }
            }
        }
//         stage("Deploy"){
//             steps{
//                 sh "docker-compose down && docker-compose up -d"
//             }
//         }
    }
}
