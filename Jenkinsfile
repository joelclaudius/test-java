pipeline {
    agent any
    stages {
        stage("maven clean") {
            steps {
                sh 'mvn clean'
            }
        }
        stage("maven install") {
            steps {
                sh 'mvn install'
            }
        }
        stage("maven package") {
            steps {
                sh 'mvn package'
            }
        }
        stage("upload artifact") {
            steps {
                nexusArtifactUploader artifacts: [[artifactId: 'bioMedical', 
                                                    classifier: '', 
                                                    file: 'target/bioMedical-0.0.2-SNAPSHOT.jar', 
                                                    type: 'jar']], 
                                      credentialsId: 'NexusID', 
                                      groupId: 'qa', 
                                      nexusUrl: 'http://198.58.119.40:8081/repository/', // Modified nexusUrl
                                      nexusVersion: 'nexus2', 
                                      protocol: 'http', 
                                      repository: 'jackie', 
                                      version: '0.0.2-SNAPSHOT'
            }
        }
    }
}
