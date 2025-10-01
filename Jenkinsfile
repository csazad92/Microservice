pipeline {
    agent any

    stages {
        stage('Deploy to Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'monitoring-test-cluster-1', contextName: '', credentialsId: 'k8s-secret', namespace: 'webapps', serverUrl: 'https://EBD4316D4C96DD0B4A1216A8DB13290A.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml "
                }
            }
        }
        stage('verify deployment') {
            steps {
               withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'monitoring-test-cluster-1', contextName: '', credentialsId: 'k8s-secret', namespace: 'webapps', serverUrl: 'https://EBD4316D4C96DD0B4A1216A8DB13290A.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
