pipeline {
    agent any

    environment {
        KUBE_CONFIG = credentials('ab27e85f-d8fe-44c5-843e-7d0bb99ad98d') 
    }

    stages {
        stage('Deploy to Kubernetes') {
            steps {
                echo "Applying Kubernetes Deployment..."
                script {
                    withCredentials([string(credentialsId: 'ab27e85f-d8fe-44c5-843e-7d0bb99ad98d', variable: 'KUBE_CONFIG_FILE')]) {
                        sh '''
                            ###
                            cp ${KUBE_CONFIG_FILE} ~/.kube/config
                            
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
