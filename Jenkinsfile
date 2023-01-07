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
        stage('Deploy') { 
            steps {
                sh './jenkins/scripts/deliver.sh' 
                input message: 'Sudah selesai menggunakan React App? (Klik "Proceed" untuk mengakhiri)' 
                sh './jenkins/scripts/kill.sh' 
            }
        }
    }
}