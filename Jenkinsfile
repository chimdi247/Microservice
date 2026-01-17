pipeline {
    agent any

    stages {
        stage('Deploy to kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://8238D4640855E313E2CB844997C15143.gr7.eu-west-2.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    sleep 60
              }
            }
        }
        
        stage('Verify deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://8238D4640855E313E2CB844997C15143.gr7.eu-west-2.eks.amazonaws.com']]) {
                    sh "kubectl get all -n webapps"
              }
            }
        }
    }
}
