pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS1p', contextName: '', credentialsId: 'k8stoken', namespace: 'webapps', serverUrl: 'https://72F6A5BAD8680B65F645C1FF04E4C58A.yl4.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS1p', contextName: '', credentialsId: 'k8stoken', namespace: 'webapps', serverUrl: 'https://72F6A5BAD8680B65F645C1FF04E4C58A.yl4.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
