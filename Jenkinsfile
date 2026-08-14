pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS_CLOUD', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://F23F4A0A428C160444399F76657CAB43.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f green-deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS_CLOUD', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://F23F4A0A428C160444399F76657CAB43.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
