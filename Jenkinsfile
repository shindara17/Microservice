pipeline {
    agent any

    stages {
        stage('EKS-Deployment') {
            steps {
                withKubeConfig(
                    caCertificate: '',
                    clusterName: 'myAppp-eks-cluster',
                    contextName: '',
                    credentialsId: 'k8s',
                    namespace: 'webapps',
                    restrictKubeConfigAccess: false,
                    serverUrl: 'https://EDC71D42CBECF00B3812584F0D3C2FB6.gr7.us-east-1.eks.amazonaws.com'
                ) {
                    script {
                        // Ensure no extra spaces in the commands
                        sh 'kubectl apply -f deployment-service.yaml'
                        sh 'kubectl get pods'
                        sh 'kubectl get svc'
                    }
                }
            }
        }
    }
}
