pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-bapi07', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://1620850AF57ECB501C3A695490E1447E.gr7.ap-southeast-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-bapi07', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://1620850AF57ECB501C3A695490E1447E.gr7.ap-southeast-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
