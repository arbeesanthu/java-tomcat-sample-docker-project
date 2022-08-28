pipeline {
    agent any
    stages {
        stage('Build Application') {
            steps {
                bat 'mvn clean package'
            }
            post {
                success {
                    echo "Now Archiving the Artifacts...."
                    archiveArtifacts artifacts: '**/*.war'
                }
            }
        }

        stage('Create Tomcat Docker Image'){
            steps {
                bat "docker build ./java-tomcat-sample-docker-project -t tomcatsamplewebapp:${env.BUILD_ID}"
            }
        }

    }
}
