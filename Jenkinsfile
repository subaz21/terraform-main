pipeline {
    agent any

    environment {
        AWS_DEFAULT_REGION = 'us-east-1'
    }

    stages {
        stage('Build') {
            steps {
                script {
                    def awsCredentials = credentials('eks-credentials') 

                    withCredentials([[$class: 'AmazonWebServicesCredentialsBinding', credentialsId: awsCredentials.id]]) {
                        sh '''
                        terraform init -upgrade
                        terraform apply -auto-approve
                        '''
                    }
                }
            }
        }
    }
}
