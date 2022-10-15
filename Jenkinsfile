    node {
      
        stage('Preparation') { 
            git credentialsId: 'GitHubAccessJenkins', url: 'https://github.com/Octobit8-DevOps/e-medics.git'
        }
        stage('Dependencies') {
               
                sh 'export JAVA_HOME=/usr/lib/jvm/java-11-openjdk-amd64'
                sh 'export PATH=$PATH:/usr/lib/jvm/java-11-openjdk-amd64/bin'
                sh 'echo $JAVA_HOME'
        }
        stage('Clean Build') {
               
                    sh "pwd"
                    sh 'ls -al'
                    sh './gradlew clean'
                   
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
