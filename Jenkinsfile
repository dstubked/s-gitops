node {
    def app

    stage('Clone repository') {
        /* Clone repository to our workspace */

        checkout scm
    }
    
    stage ('Deploy Policy') {
        /* Deploy runtime policy */
        withCredentials([usernameColonPassword(credentialsId: 'aquaui', variable: 'aquauipass')]) {
            sh "curl -H 'Content-Type: application/json' -X PUT -u $aquauipass -d @scb-demo-policy.json http://35.223.9.143:8080/api/v2/runtime_policies/demo-policy"
        }
    }
    stage ('Validate Policy') {
        /* Deploy runtime policy */
        withCredentials([usernameColonPassword(credentialsId: 'aquaui', variable: 'aquauipass')]) {
            sh "curl -H 'Content-Type: application/json' -X GET -u $aquauipass http://35.223.9.143:8080/api/v2/runtime_policies/demo-policy | jq"
        }
    }    
}
