pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'ccit-eks-cluster1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://C780CF283691E314A4CBBED6578A1352.gr7.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'ccit-eks-cluster1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://C780CF283691E314A4CBBED6578A1352.gr7.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
