pipeline {
    agent any
    environment{
        registry = "noahross/udacity-nd9991-capstone"
        credentials = "dockercreds"
        dockerImage = ''
    }
    stages {
        stage("Lint HTML") {
            steps {
                sh 'tidy -q -e src/*.html'
            }
        }
        stage("Clone Repo"){
            steps {
                checkout scm
            }
        }
        stage("Build Image"){
            steps {
                script {
                    dockerImage = docker.build registry + ":latest"
                }
            }
        }
        stage('Push Image') {
            steps{
                script {
                    docker.withRegistry( '', credentials ) {
                        dockerImage.push()
                    }
                }
            }
        }
        stage("Remove Image Locally"){
            steps {
                sh "docker rmi $registry:latest"
                sh "docker rmi nginx:alpine"
            }
        }
        stage("Deploy to Kubernetes Cluster"){
            steps {
                withAWS(credentials: 'awscreds', region: 'us-west-2') {
                    sh "aws eks --region us-west-2 update-kubeconfig --name udacity-eks-cluster"
                    sh "kubectl apply -f infrastructure/app-deployment.yaml"
                    sh "kubectl get svc"
                }
            }
        }
    }
}