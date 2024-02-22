pipeline{
    agent any

    environment{
        nexus_url = "198.58.119.40:8081"
        version = "0.0.4-SNAPSHOT"
        repo="jackie"
        file_target = "target/bioMedical-0.0.2-SNAPSHOT.jar"
        group_id = "dev"
        file_type = "jar"
        credentials_id ="NexusID"
        protocol = "http"
        artifact_id = "bioMedical"
    }
    stages{
        stage("maven clean"){
            steps{
                sh 'mvn clean'
            }
        }
        stage("maven install"){
            steps{
                sh 'mvn install'
            }
            
        }
        stage("maven package"){
            steps{
                sh 'mvn package'
            }
        }
        stage("upload artifact"){
            steps{
                nexusArtifactUploader artifacts: [[artifactId: ${artifact_id}, 
                classifier: '', 
                file: ${file_target}, 
                type: ${file_type}]], 
                credentialsId: ${credentials_id}, 
                groupId: ${group_id}, 
                nexusUrl: ${nexus_url}, 
                nexusVersion: ${version}, 
                protocol: ${protocol}, 
                repository: ${repo}, 
                version: ${version}
            }
        }
    }
}