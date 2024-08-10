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
                    // Print all environment variables available in Jenkins
                    echo "Printing all environment variables:"
                    env.each { k, v -> echo "${k} = ${v}" }

                    // Print specific environment variable (e.g., PATH)
                    if (isUnix()) {
                        // On Unix-based systems
                        sh 'echo $PATH'
                    } else {
                        // On Windows systems
                        bat 'echo %PATH%'
                    }
                }
            }
        }
    }
}
