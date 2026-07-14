pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'MYEKS', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://CAD32FDB137C379F926238C1FC163A4A.gr7.eu-north-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'MYEKS', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://CAD32FDB137C379F926238C1FC163A4A.gr7.eu-north-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
