pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS_CLOUD', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://00DE7062FE51B9C6C04642DEF15F4138.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS_CLOUD', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://00DE7062FE51B9C6C04642DEF15F4138.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
