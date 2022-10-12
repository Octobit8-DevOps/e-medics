pipeline {
    agent { label 'master' }

    stages {
        stage('Checkout') {
            steps {
                sh 'git clone https://github.com/Octobit8-DevOps/e-medics.git'
            }
        }
        stage('Build') {
            steps {
                sh 'gradle build'
            }
        }
    }
}