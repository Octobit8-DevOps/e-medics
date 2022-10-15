    node {
      
        stage('Preparation') { 
            git credentialsId: 'GitHubAccessJenkins', url: 'https://github.com/Octobit8-DevOps/e-medics.git'
        }
        stage('Dependencies') {
                sh 'sudo npm install -g react-native-cli'
                sh 'npm install'
                sh 'react-native link'
                sh 'export JAVA_HOME=/opt/jdk1.8.0_201'
                sh 'export JRE_HOME=/opt/jdk1.8.0_201/jre'
                sh 'export PATH=$PATH:/opt/jdk1.8.0_201/bin:/opt/jdk1.8.0_201/jre/bin'
                sh 'echo $JAVA_HOME'
        }
        stage('Clean Build') {
                dir("android") {
                    sh "pwd"
                    sh 'ls -al'
                    sh './gradlew clean'
                }   
        }
        
        stage('Build release ') {
            parameters {
                credentials credentialType: 'org.jenkinsci.plugins.plaincredentials.impl.FileCredentialsImpl', defaultValue: '5d34f6f7-b641-4785-frd5-c93b67e71b6b', description: '', name: 'keystore', required: true
            }
            dir("android") {
                sh './gradlew assembleRelease'
            }
        }
      
        stage('Compile') {
            archiveArtifacts artifacts: '**/*.apk', fingerprint: true, onlyIfSuccessful: true            
        }
   
    }
