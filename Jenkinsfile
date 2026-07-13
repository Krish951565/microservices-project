pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'MYEKS', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://5E13761DB592EA6B0956A324A60E0967.sk1.eu-north-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'MYEKS', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://5E13761DB592EA6B0956A324A60E0967.sk1.eu-north-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
