pipeline {
    agent {
        docker {
            image'node:lts-buster'
            args'-p 3000:3000'
        }
    }
    stages {
        stage('Build') {
            steps {
                sh'npm install'
            }
        }
        stage('Test') {
            steps {
                sh'./jenkins/scripts/test.sh'
            }
        }
        stage('Approval Deploy') {
            steps {
                input message: 'Lanjutkan ke tahap deploy ? (Klik "Proceed" untuk mengakhiri)'
            }
        }
        stage('Deploy') {
            steps {
                sh'./jenkins/scripts/deliver.sh'
                sh'sleep 60'
                sh'./jenkins/scripts/kill.sh'
            }
        }
    }
}