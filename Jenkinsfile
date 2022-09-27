pipeline {
    agent any 
    stages {
        stage("verify tooling") {
            steps {
                sh '''
                docker version
                docker info 
                docker compose virsion
                curl --virsion
                jq --virsion
                '''
            }
        }
    }
}