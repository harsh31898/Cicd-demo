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
                docker build -t demo-${env.BRANCH_NAME} .
                """
                }
            }
        }
        stage('Docker Run'){
         steps{
            script{
            sh """
               docker run --rm cicd-demo:${BRANCH_NAME}
            """
            }
         }
        }


    }
}