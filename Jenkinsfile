pipeline {
    agent any
    tools {
        git 'Default'  // or specify the Git tool you've configured
    }
    environment {
        DOCKERHUB_CREDENTIALS = credentials('dockerhub-credentials-id-ec2') // DockerHub credentials stored in Jenkins
        DOCKER_IMAGE = 'thethymca/my-node-app'
        DOCKER_TAG = 'latest'
    }
    
    stages {
        
       stage('Build the Image') {
            steps{
                withDockerRegistry( url: 'https://index.docker.io/v1/', credentialsId: 'dockerhub-credentials-id-ec2') {
                    sh '''
                        docker build -t thethymca/my-node-app-1:latest . 
                        docker push thethymca/my-node-app-1:latest
                    '''
                } 
            }
       }    
    }
    
    /*post {
        always {
            cleanWs()  // Clean the workspace after pipeline execution
        }
    }*/
    
}
