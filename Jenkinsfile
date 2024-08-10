pipeline {
    agent any
    parameters {
        choice choices: ['PROD', 'UAT', 'QA'], description: 'The relevant environment for the build and deployment', name: 'ENV'
        string description: 'The version that is about to be built and deployed', name: 'Version'
        string(name: 'KEY_VALUE_JSON', defaultValue: '[

  { "Type": "TypeA", "Evidences": ["a", "b", "c"] },

  { "Type": "TypeB", "Evidences": ["d", "e"] },

  { "Type": "TypeA", "Evidences": ["c", "f", "g"] },

  { "Type": "TypeB", "Evidences": ["k", "m", "l"] },

  { "Type": "TypeA", "Evidences": ["f", "n" ] }

]
', description: 'Enter a JSON object as a string (e.g., {"key1":"value1","key2":"value2"})')
        
    }
    stages {
        stage('Build') {
            steps {
                // Use double quotes and ${} for interpolation
                checkout scmGit(branches: [[name: "*/${params.ENV}"]], extensions: [], userRemoteConfigs: [[credentialsId: '92ed90ec-a7e1-42b2-bcde-e4279aab4fb8', url: 'https://github.com/DanielShepelev/training']])
            }
        }
        stage('env vars list') {
            steps {
                sh "printenv | sort"
            }
        }
        stage('Example Deploy') {
            steps {
                script {
                    sh "bash hello.sh" 
                }
            }
        }
    }
}
