pipeline {
    agent any
    parameters {
        choice choices: ['PROD', 'UAT', 'QA'], description: 'The relevant environment for the build and deployment', name: 'ENV'
        string description: 'The version that is about to be built and deployed', name: 'Version'
    }
    stages {
        stage('Build') {
            steps {
                checkout scmGit(branches: [[name: '*/{params.ENV}']], extensions: [], userRemoteConfigs: [[credentialsId: '92ed90ec-a7e1-42b2-bcde-e4279aab4fb8', url: 'https://github.com/DanielShepelev/training']])
            }
        }
        stage('Example Deploy') {
            steps {
                script {
                    sh "printenv" 
                    }
                }
            }
        }
    }
// defwed
