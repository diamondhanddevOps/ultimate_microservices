pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                script {
                    withKubeConfig(
                        credentialsId: 'k8-token',
                        serverUrl: 'https://53E678C3A4D461B399B229688F6FC3EB.gr7.us-east-1.eks.amazonaws.com',
                        clusterName: 'Abi-EKS',
                        namespace: 'webapps'
                    ) {
                        sh "kubectl apply -f deployment-service.yml"
                        sleep 60
                    }
                }
            }
        }

        stage('Verify Deployment') {
            steps {
                script {
                    withKubeConfig(
                        credentialsId: 'k8-token',
                        serverUrl: 'https://53E678C3A4D461B399B229688F6FC3EB.gr7.us-east-1.eks.amazonaws.com',
                        clusterName: 'Abi-EKS',
                        namespace: 'webapps'
                    ) {
                        sh "kubectl get svc -n webapps"
                    }
                }
            }
        }
    }
}
