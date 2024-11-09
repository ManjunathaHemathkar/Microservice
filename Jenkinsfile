pipeline {
    agent any

    stages {
        stage('Deploy to Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-2', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://5308CD02E4277E21D5A59D5794D73012.gr7.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                }
            }
        }
        
        stage('Hello') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-2', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://5308CD02E4277E21D5A59D5794D73012.gr7.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
