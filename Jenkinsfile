pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'MYEKS', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://C761D5CFAFB1771DB04A72DDB3B9E443.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'MYEKS', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://C761D5CFAFB1771DB04A72DDB3B9E443.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
