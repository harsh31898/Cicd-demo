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
                docker build -t  cicd-demo:${env.BRANCH_NAME} .
                """
                }
            }
        }
        stage('Docker Run'){
         steps{
            script{
            sh """
               docker run --rm cicd-demo:${env.BRANCH_NAME}
            """
            }
         }
        }


    }
}