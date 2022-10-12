pipeline {
    agent { label 'master' }

    stages {
        stage('Checkout') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[credentialsId: 'GitHubAccess', url: 'https://github.com/Octobit8-DevOps/e-medics.git']]])
            }
        }
        stage('Build') {
            steps {
                sh 'chmod 777 gradlew'
                sh './gradlew clean'
            }
        }
    }
    
}
