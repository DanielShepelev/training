pipeline {
    agent any
    parameters {
        choice choices: ['PROD', 'UAT', 'QA'], description: 'The relevant environment for the build and deployment', name: 'ENV'
        string description: 'The version that is about to be built and deployed', name: 'Version'
    }
    stages {
        stage('Build') {
            steps {
                echo params.ENV
            }
        }
        stage('Example Deploy') {
            steps {
                script {
                    def envVars = System.getenv()
                    envVars.each { k, v -> echo "${k} = ${v}" }
                }
            }
        }
    }
}
