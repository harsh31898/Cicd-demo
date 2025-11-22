pipeline {
    agent any

    stages {
        stage('Checkour') {
            steps {
               checkout scm
            }
        }
        stage('Docker build'){
            steps{
                script
                {
                sh """
                docker build -t  cicd-demo:${env.BUILD_NUMBER} .
                """
                }
            } 
        }
         stage('Deploy to Kubernetes') {
            steps {
                script {
            sh """
               ls -lrt
               sed -i 's/image_tag/${env.BUILD_NUMBER}/g' k8s/Deployment.yaml
               kubectl apply -f k8s/
            """
            }
         }
        }


    }
}