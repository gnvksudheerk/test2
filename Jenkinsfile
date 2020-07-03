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
                script{
                    def mavenPom = readMavenPom file:'pom.xml'
                    nexusArtifactUploader artifacts: [[
                    artifactId: 'test2',
                    classifier: '',
                    file: "target/test2-${mavenPom.version}.jar",
                    type: 'jar']],
                    credentialsId: 'nexus3',
                    groupId: 'org.example',
                    nexusUrl: '18.130.9.16:8081',
                    nexusVersion: 'nexus3',
                    protocol: 'http',
                    repository: 'testapp-release',
                    version: "${mavenPom.version}"
                }
            }
        }
    }
}