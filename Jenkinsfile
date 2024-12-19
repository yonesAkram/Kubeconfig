
pipeline {
    agent any

    environment {
        KUBE_CONFIG = credentials('6440e0ec-6cd7-4738-80b2-8ba7b8afe427') 
    }

        stages {
          
        stage('Deploy to Kubernetes') {
            steps {
                echo "Applying Kubernetes Deployment..."
                script {
                    withEnv(["KUBECONFIG=${KUBE_CONFIG}"]) {
                        sh '''
                                      
                            kubectl apply -f sec.yaml -n all

                            kubectl get pods -n all
                            kubectl get services -n all
                        '''
                    }
                }
            }
        }
    }
}
