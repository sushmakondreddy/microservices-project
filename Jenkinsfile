pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'MYEKS', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://F12C3FD27BC33F5B93F54DEA9180F0E6.yl4.us-east-1.eks.amazonaws.comm']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'MYEKS', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://F12C3FD27BC33F5B93F54DEA9180F0E6.yl4.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
