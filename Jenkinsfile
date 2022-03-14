pipeline {
    agent any 
    environment {
    DOCKERHUB_CREDENTIALS = credentials('pratik-dockerhub')
    }
    stages { 
        stage('SCM Checkout') {
            steps{
            git 'https://github.com/deshmukhpratik/Nodejs-docker.git'
            }
        }

        stage('Build docker image') {
            steps {  
                sh 'docker build -t pratik2741999/nodeapp:$BUILD_NUMBER .'
            }
        }
        stage('login to dockerhub') {
            steps{
                sh 'docker login -u $DOCKERHUB_CREDENTIALS_USR --password Pratik@27'
            }
        }
        stage('push image') {
            steps{
                sh 'docker push pratik2741999/nodeapp:$BUILD_NUMBER'
            }
        }
}
post {
        always {
            sh 'docker logout'
        }
    }
}

