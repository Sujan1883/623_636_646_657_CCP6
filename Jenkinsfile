pipeline {
    agent any
    stages {
        stage('Build Docker Images') {
            steps {
                script {
                    bat 'docker build -t sujandkripadas/frontend-deploy ./frontend'
                    bat 'docker build -t sujandkripadas/auth-deploy ./authenticate'
                    bat 'docker build -t sujandkripadas/cart-deploy ./cart'
                    bat 'docker build -t sujandkripadas/items-deploy ./items'
                    bat 'docker build -t sujandkripadas/order-deploy ./order'
                }
            }
        }
        stage('Deploy') {
            steps {
                script {
                    bat 'kubectl delete deployments --all'
                    bat 'kubectl delete services --all'
                    bat 'kubectl apply -f ./k8s/'
                }
            }
        }
    }
}
