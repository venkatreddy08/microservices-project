pipeline {
    agent any

    stages {
        stage('Build & Tag Docker Image') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                        sh "docker build -t venkatreddy08/recommendationservice:latest ."
                    }
                }
            }
        }
        stage('Trivy Scan') {
         steps{
             sh "trivy image venkatreddy08/recommendationservice:latest"
         }
        }
        stage('Push Docker Image') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                        sh "docker push venkatreddy08/recommendationservice:latest "
                    }
                }
            }
        }
    }
}
