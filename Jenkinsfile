pipeline {
    agent any

    stages {
        stage('Build & Tag Docker Image') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'Docker', toolName: 'Docker') {
                        sh "docker build -t shittuay/currencyservice:latest ."
                    }
                }
            }
        }
        
        stage('Push Docker Image') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'Docker', toolName: 'Docker') {
                        sh "docker push shittuay/currencyservice:latest "
                    }
                }
            }
        }
    }
}
