pipeline {
    agent any
    stages {
        stage("Lint HTML") {
            steps {
                sh 'tidy -q -e src/*.html'
            }
        }
        // stage("Upload to AWS") {
        //     steps {
        //         withAWS(region:'us-east-2',credentials:'aws-static') {
        //             // do something
        //             s3Upload(file:'index.html', bucket:'jenkins-test-aws-static-noah-ross', path:'index.html')
        //         }
        //     }
        // }
    }
}