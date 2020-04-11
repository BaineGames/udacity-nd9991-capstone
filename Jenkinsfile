pipeline {
    agent any
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
                sh '''
                    sudo docker build -t noahross/udacity-nd9991-capstone .
                    sudo docker images
                '''
            }
        }

    }
}