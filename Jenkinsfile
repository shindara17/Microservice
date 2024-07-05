pipeline {
    agent any
    environment {
        SCANNER_HOME = tool 'sonar-scanner'

   }

    stages {
            stage('SonarQube') {
             steps {
                withSonarQubeEnv('sonar-scanner') {
                    sh '''$SCANNER_HOME/bin/sonar-scanner -Dsonar.projectKey=Microservice-Deployment -Dsonar.ProjectName=Microservice-Deployment -Dsonar.java.binaries=.'''
                }
            }
        }
            stage('adservice') {
              steps {
               script {
                 withDockerRegistry(credentialsId: 'dockerpass', toolName: 'docker') {
                    dir('/var/lib/jenkins/workspace/Microservice-Deployment/src/adservice/') {
                        sh "docker build -t shindara17/adservice:latest ."
                        sh "docker push shindara17/adservice:latest"
                        sh "docker rmi shindara17/adservice:latest"
                        sh 'docker system prune -a -f --volumes'
                    }
                }
            }
        }
            }
            stage('cartservice') {
              steps {
               script {
                 withDockerRegistry(credentialsId: 'dockerpass', toolName: 'docker') {
                    dir("/var/lib/jenkins/workspace/Microservice-Deployment/src/cartservice/src/") {
                        sh "docker build -t shindara17/cartservice:latest ."
                        sh "docker push shindara17/cartservice:latest"
                        sh "docker rmi shindara17/cartservice:latest"
                        sh 'docker system prune -a -f --volumes'
                    }
                }
            }
        }
       }
            stage('checkoutservice') {
              steps {
               script {
                 withDockerRegistry(credentialsId: 'dockerpass', toolName: 'docker') {
                    dir("/var/lib/jenkins/workspace/Microservice-Deployment/src/checkoutservice/") {
                        sh "docker build -t shindara17/checkoutservice:latest ."
                        sh "docker push shindara17/checkoutservice:latest"
                        sh "docker rmi shindara17/checkoutservice:latest"
                        sh 'docker system prune -a -f --volumes'
                    }
                }
            }
        }
            }
            stage('currencyservice') {
              steps {
               script {
                 withDockerRegistry(credentialsId: 'dockerpass', toolName: 'docker') {
                    dir("/var/lib/jenkins/workspace/Microservice-Deployment/src/currencyservice/") {
                        sh "docker build -t shindara17/currencyservice:latest ."
                        sh "docker push shindara17/currencyservice:latest"
                        sh "docker rmi shindara17/currencyservice:latest"
                        sh 'docker system prune -a -f --volumes'
                    }
                }
            }
        }

            }
            stage('emailservice') {
              steps {
               script {
                 withDockerRegistry(credentialsId: 'dockerpass', toolName: 'docker') {
                    dir("/var/lib/jenkins/workspace/Microservice-Deployment/src/emailservice/") {
                        sh "docker build -t shindara17/emailservice:latest ."
                        sh "docker push shindara17/emailservice:latest"
                        sh "docker rmi shindara17/emailservice:latest"
                        sh 'docker system prune -a -f --volumes'
                    }
                }
            }
        }
            }
            stage('frontend') {
              steps {
               script {
                 withDockerRegistry(credentialsId: 'dockerpass', toolName: 'docker') {
                    dir("/var/lib/jenkins/workspace/Microservice-Deployment/src/frontend/") {
                        sh "docker build -t shindara17/frontend:latest ."
                        sh "docker push shindara17/frontend:latest"
                        sh "docker rmi shindara17/frontend:latest"
                        sh 'docker system prune -a -f --volumes'
                    }
                }
            }
        }
            }
            stage('loadgenerator') {
              steps {
               script {
                 withDockerRegistry(credentialsId: 'dockerpass', toolName: 'docker') {
                    dir("/var/lib/jenkins/workspace/Microservice-Deployment/src/loadgenerator/") {
                        sh "docker build -t shindara17/loadgenerator:latest ."
                        sh "docker push shindara17/loadgenerator:latest"
                        sh "docker rmi shindara17/loadgenerator:latest"
                        sh 'docker system prune -a -f --volumes'
                    }
                }
            }
        }
            }
             stage('paymentservice') {
              steps {
               script {
                 withDockerRegistry(credentialsId: 'dockerpass', toolName: 'docker') {
                    dir("/var/lib/jenkins/workspace/Microservice-Deployment/src/paymentservice/") {
                        sh "docker build -t shindara17/paymentservice:latest ."
                        sh "docker push shindara17/paymentservice:latest"
                        sh "docker rmi shindara17/paymentservice:latest"
                        sh 'docker system prune -a -f --volumes'
                    }
                }
            }
        }
             }
             stage('productcatalogservice') {
              steps {
               script {
                 withDockerRegistry(credentialsId: 'dockerpass', toolName: 'docker') {
                    dir("/var/lib/jenkins/workspace/Microservice-Deployment/src/productcatalogservice/") {
                        sh "docker build -t shindara17/productcatalogservice:latest ."
                        sh "docker push shindara17/productcatalogservice:latest"
                        sh "docker rmi shindara17/productcatalogservice:latest"
                        sh 'docker system prune -a -f --volumes'
                    }
                }
            }
        }
             }
             stage('recommendationservice') {
              steps {
               script {
                 withDockerRegistry(credentialsId: 'dockerpass', toolName: 'docker') {
                    dir("/var/lib/jenkins/workspace/Microservice-Deployment/src/recommendationservice/") {
                        sh "docker build -t shindara17/recommendationservice:latest ."
                        sh "docker push shindara17/recommendationservice:latest"
                        sh "docker rmi shindara17/recommendationservice:latest"
                        sh 'docker system prune -a -f --volumes'
                    }
                }
            }
        }
             }
             stage('shippingservice') {
              steps {
               script {
                 withDockerRegistry(credentialsId: 'dockerpass', toolName: 'docker') {
                    dir("/var/lib/jenkins/workspace/Microservice-Deployment/src/shippingservice/") {
                        sh "docker build -t shindara17/shippingservice:latest ."
                        sh "docker push shindara17/shippingservice:latest"
                        sh "docker rmi shindara17/shippingservice:latest"
                        sh 'docker system prune -a -f --volumes'
                    }
                }
            }
        }
    }

              stage('EKS-Deployment') {
            steps {
                withKubeConfig(caCertificate: '', clusterName: ' myAppp-eks-cluster', contextName: '', credentialsId: 'k8s', namespace: 'webapps', restrictKubeConfigAccess: false, serverUrl: 'https://A50566454B6F686256D7FFCCFA22E82B.gr7.us-east-1.eks.amazonaws.com') {
                    sh 'kubectl apply -f deployment-service.yaml'
                    sh 'kubectl get pods'
                    sh 'kubectl get svc'

                }
                }
            }
        }
   }
