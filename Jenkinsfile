pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-pushpa1', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://7503ACF05FECB52C40452A5014B133BB.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-pushpa1', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://7503ACF05FECB52C40452A5014B133BB.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
