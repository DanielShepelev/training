pipeline {
    agent any
    parameters {
        choice(choices: ['PROD', 'UAT', 'QA'], description: 'The relevant environment for the build and deployment', name: 'ENV')
        string(description: 'The version that is about to be built and deployed', name: 'Version')
        password(name: 'PASSWORD', defaultValue: 'SECRET', description: 'Enter a password')
        text(name: 'KEY_VALUE_JSON', defaultValue: '''[
  { "Type": "TypeA", "Evidences": ["a", "b", "c"] },
  { "Type": "TypeB", "Evidences": ["d", "e"] },
  { "Type": "TypeA", "Evidences": ["c", "f", "g"] },
  { "Type": "TypeB", "Evidences": ["k", "m", "l"] },
  { "Type": "TypeA", "Evidences": ["f", "n" ] }
]''', description: 'Enter a JSON object as a string (e.g., [{ "Type": "TypeA", "Evidences": ["a", "b"] }])')
    }
    
    
    stages {
        stage('Groovy practice'){
            steps{
                script{
                def jsonSlurper = new groovy.json.JsonSlurper()
                def keyValueList = jsonSlurper.parseText(params.KEY_VALUE_JSON)
                def fullList = []
                for(int i = 0;i<keyValueList.size;i++) {
                     for(int j = 1;j<keyValueList.size;j++) {
                         if(keyValueList[i]["Type"] ==  keyValueList[j]["Type"]){
                             if(!([keyValueList[i]["Evidences"]].disjoint(keyValueList[j]["Evidences"]))){
                                 for(item in keyValueList[i]["Evidences"]){
                                     fullList.add(item)
                                 }
                                 for(item in keyValueList[j]["Evidences"]){
                                     fullList.add(item)
                                 }
                                 
                             }
                         }
                         println(fullList)
                         fullList.clear()
                      }
                  }
                }
                
            }
            }
        }










        
        // stage('Build') {
        //     steps {
        //         checkout scmGit(branches: [[name: "*/${params.ENV}"]], extensions: [], userRemoteConfigs: [[credentialsId: '92ed90ec-a7e1-42b2-bcde-e4279aab4fb8', url: 'https://github.com/DanielShepelev/training']])
        //     }
        // }   
        // stage('Example') {
        //     input {
        //         message "Should we continue?"
        //         ok "Yes, we should."
        //         submitter "alice,bob"
        //         parameters {
        //             string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')
        //         }
        //     }
        //     steps {
        //         echo "Hello, ${PERSON}, nice to meet you."
        //     }
        // }

        // stage('Parse and Process JSON') {
        //     steps {
        //         script {
        //             // Parse the JSON string into a list of maps
        //             def jsonSlurper = new groovy.json.JsonSlurper()
        //             def keyValueList = jsonSlurper.parseText(params.KEY_VALUE_JSON)

        //             // Iterate over the list and print the Type and Evidences
        //             keyValueList.each { entry ->
        //                 echo "Type: ${entry.Type}"
        //                 echo "Evidences: ${entry.Evidences[1]}"
        //             }
        //         }
        //     }
        // }
        // stage('env vars list') {
        //     steps {
        //         sh "printenv | sort"
        //     }
        // }
        // stage('Example Deploy') {
        //     environment {
        //         SERVICE_CREDS = credentials('GitHub_connection')
        //     }
        //     steps {
        //         script {
        //             echo "Password: ${params.PASSWORD}"
        //         }
        //     }
        // }
    }
  
