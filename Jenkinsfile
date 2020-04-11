pipeline {
    agent any
    stages {
        stage("Lint HTML") {
            steps {
                sh 'tidy -q -e src/*.html'
            }
        }
        stage("Clone Repo"){
            checkout scm
        }
        stage("Build Image"){
        }
        stage("Push Image"){
            
        }
        stage("Set Context"){
            
        }
        stage("Deploy Image"){
            
        }
    }
}