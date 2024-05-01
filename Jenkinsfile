pipeline {
    agent any

    stages {
        stage('Build & Tag Docker Image') {
            steps {
                script {
                    dir('src') {

                    withDockerRegistry(credentialsId: 'Docker', toolName: 'Docker') {
                        sh "docker build -t shittuay/cartservice:latest ."
                    }
                        }
                }
            }
        }
        
        stage('Push Docker Image') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'Docker', toolName: 'Docker') {
                        sh "docker push shittuay/cartservice:latest "
                    }
                }
            }
        }
    }
}
