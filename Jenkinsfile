pipeline {
    agent any 
    stages {
        stage('verify tooling') {
            steps {
                sh '''
                docker version
                docker info 
                docker compose version
                curl --version
                jq --version
                '''
            }
        }
        stage('Prune docker data') {
            steps {
                sh 'docker system prune -a --volumes -f'
            }
        }
        stage('start container') {
            steps {
                sh 'docker compose up -d --no-color --wait'
                sh 'docker compose ps'
            }
        }
        stage('Run test againets the container') {
            steps {
                sh 'curl http://localhost:3000/param?query=demo | jq'
            }
        }
    }
    post {
        always {
            sh 'docker compose down --remove-orphans -v'
            sh 'docker compose ps'
        }
    }
}