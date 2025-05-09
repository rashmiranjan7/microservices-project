pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-raham1', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://92548CCD42257FB7AD83F4412E387E9E.gr7.ap-southeast-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-raham1', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://92548CCD42257FB7AD83F4412E387E9E.gr7.ap-southeast-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
