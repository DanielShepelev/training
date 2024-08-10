pipeline {
    agent any
    parameters {
        choice choices: ['PROD', 'UAT', 'QA'], description: 'The relevant environment for the build and deployment', name: 'ENV'
        string description: 'The version that is about to be built and deployed', name: 'Version'
    }
    stages {
        stage('Build') {
            steps {
                echo "ENV Parameter: ${params.ENV}"
                echo "Version Parameter: ${params.Version}"
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
}
