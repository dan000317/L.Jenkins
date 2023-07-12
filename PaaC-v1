pipeline {
    agent any
    tools {
        maven "MAVEN3"
        jdk "OracleJDK8"
    }

    stages {
        stage ('Fetch Code'){
            steps{
                git branch: 'vp-rem', 
                url: 'https://github.com/devopshydclub/vprofile-repo.git'
            }
        }
        stage ('Build'){
            steps{
                sh 'mvn install -DskipTests'
            }
            post{
                success{
                    echo 'Archiving Artifacts now.'
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }
        stage('Unit Test'){
            steps{
                sh 'mvn test'
            }
            
        }
    }
}
