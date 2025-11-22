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
               sed -i 's/image_tag/${env.BUILD_NUMBER}/g' k8s/deployment.yaml
               kubectl apply -f k8s/
            """
            }
         }
        }


    }
}