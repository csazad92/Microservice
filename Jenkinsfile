pipeline {
    agent any

    stages {
        stage('Deploy to Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: ' monitoring-test-cluster-1', contextName: '', credentialsId: 'k8s-Secret', namespace: 'webapps', serverUrl: 'https://47C8459269CE60DFF8A2C1C8B053077E.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
            }
        }
    }
        stage('Verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: ' monitoring-test-cluster-1', contextName: '', credentialsId: 'k8s-Secret', namespace: 'webapps', serverUrl: 'https://47C8459269CE60DFF8A2C1C8B053077E.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl get all -n webapps"
                }
            }
        }
    }
}
