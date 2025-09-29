pipeline {
    agent any

    stages {
        stage('Deploy to kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: ' eksctl-monitoring-test-cluster-1-cluster', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'arn:aws:cloudformation:us-east-1:739275449568:stack/eksctl-monitoring-test-cluster-1-cluster/f9c72170-9ceb-11f0-93a9-0e6ee1ba55f5']]) { 
                sh "kubectl apply -f deployment.yml"
            }
        }
    }     
    
        stage('Verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: ' eksctl-monitoring-test-cluster-1-cluster', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'arn:aws:cloudformation:us-east-1:739275449568:stack/eksctl-monitoring-test-cluster-1-cluster/f9c72170-9ceb-11f0-93a9-0e6ee1ba55f5']]) {
                    sh "Kubectl get all -n webapps"

                }
            }
        }
    }
}
