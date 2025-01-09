pipeline {
    agent any
    tools {
        maven 'maven3'
        jdk 'java17'
    }
    stages {
        stage('Download Code From Git') {
            steps {
                git branch: 'main', url: 'https://github.com/drjineshshahbds/maven-jenkins6.git'
            }
        }
        stage('Build Java Project') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage('Archieve Artifacts') {
            steps {
                archiveArtifacts artifacts: '**/*.war', followSymlinks: false
            }
        }
        stage('Build Another Project') {
            steps {
                build wait: false, job: 'deploy-to-dev-pipeline'
            }
        }
    }
}
