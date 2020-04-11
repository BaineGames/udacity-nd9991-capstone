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

                echo "test"
                script {
                    dockerImage = docker.build registry + ":$BUILD_NUMBER"
                }
            }
        }stage("Push Image"){
            sh 'docker images'
        }

    }
}