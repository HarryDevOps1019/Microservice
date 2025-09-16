pipeline {
    agent any

    stages {
        stage('Deploy to Kubernets') {
            steps {
                withKubeConfig(caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'ks8_token', namespace: 'webapps', restrictKubeConfigAccess: false, serverUrl: 'https://8248E30CC0242AADFBCBC6040C343F56.gr7.ap-south-1.eks.amazonaws.com') {
                    sh"kubectl apply -f deployment-service.yml"
                }
            }
        }
        
        stage('verify deployment') {
            steps {
                withKubeConfig(caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'ks8_token', namespace: 'webapps', restrictKubeConfigAccess: false, serverUrl: 'https://8248E30CC0242AADFBCBC6040C343F56.gr7.ap-south-1.eks.amazonaws.com') {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
