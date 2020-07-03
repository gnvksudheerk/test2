pipeline {
    agent any
    tools {
      maven 'Maven3'
    }
    stages{
        stage('Build'){
            steps{
                sh script: 'mvn clean package'
            }
        }
        stage('Upload jar to Nexus'){
            steps{
                nexusArtifactUploader artifacts: [[
                artifactId: 'test2',
                classifier: '',
                file: 'target/test2-1.0.1.jar',
                type: 'jar']],
                credentialsId: 'nexus3',
                groupId: 'org.example',
                nexusUrl: '18.130.9.16:8081',
                nexusVersion: 'nexus3',
                protocol: 'http',
                repository: 'testapp-release',
                version: '1.0.0'
            }
        }
    }
}