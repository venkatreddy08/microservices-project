pipeline {
    agent any

    stages {
        stage('Build & Tag Docker Image') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                        sh "docker build -t venkatreddy08/paymentservice:latest ."
                    }
                }
            }
        }
        stage('Trivy Scan') {
         steps{
             sh "trivy image venkatreddy08/paymentservice:latest"
         }
        }
        stage('Push Docker Image') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                        sh "docker push venkatreddy08/paymentservice:latest "
                    }
                }
            }
        }
    }
}
