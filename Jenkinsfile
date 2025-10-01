pipeline {
    agent any

    stages {
        stage('Deploy to kubernetes') {
            steps {
               withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: ' monitoring-test-cluster-1', contextName: '', credentialsId: 'k8s-secret', namespace: 'webapps', serverUrl: 'https://6D42C7CB29DE729CEBBD98A6E1DD4503.gr7.us-east-1.eks.amazonaws.com']]) {
                sh "kubectl apply -f deployment-service.yml"
                }
            }
        }
        
        stage('verify deployment')) {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: ' monitoring-test-cluster-1', contextName: '', credentialsId: 'k8s-secret', namespace: 'webapps', serverUrl: 'https://6D42C7CB29DE729CEBBD98A6E1DD4503.gr7.us-east-1.eks.amazonaws.com']]) {
                 sh "kubectl get svc -n webapps"
                 }
            }
        }
    }
}
