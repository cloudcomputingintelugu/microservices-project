pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'ccit-eks-cluster1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://810501B8B78A19C0A2253A1FAE223EFF.gr7.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'ccit-eks-cluster1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://810501B8B78A19C0A2253A1FAE223EFF.gr7.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
