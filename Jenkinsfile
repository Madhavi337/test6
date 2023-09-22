pipeline {
    agent any
    stages {
        stage('Call First Endpoint') { // Give it a unique name
            steps {
                script {
                    def response = httpRequest(
                        url: 'https://localhost:9164/management/login',
                        httpMode: 'GET',
                        customHeaders: [[name: "Authorization", value: "Basic YWRtaW46YWRtaW4="]],
                        acceptType: 'APPLICATION_JSON',
                        responseHandle: 'NONE',
                        timeout: 60,
                        validResponseCodes: '200',
                        ignoreSslErrors: true,
                    )

                    // Capture the response status code and content
                    def statusCode = response.getStatus()
                    def responseBody = response.getContent()

                    echo "Response Status Code: ${statusCode}"
                    echo "Response Body: ${responseBody}"

                    // You can now process or parse the response as needed
                    // For example, parsing JSON:
                    def jsonResponse = new groovy.json.JsonSlurper().parseText(responseBody)
                    echo "Parsed JSON Response: ${jsonResponse}"


                    if (statusCode == 200) {
                        def jsonResponse = new groovy.json.JsonSlurper().parseText(responseBody)
                        def accessTokenValue = jsonResponse.AccessToken
                        echo "AccessToken: ${accessTokenValue}"
                    }
                    
                }
            }
        }
        stage('Call Second Endpoint') { // Give it a unique name
            steps {
                script {
                    def res = httpRequest(
                        url: 'https://localhost:9164/management/login',
                        httpMode: 'GET',
                        customHeaders: [[name: "Authorization", value: "Basic YWRtaW46YWRtaW4="]],
                        acceptType: 'APPLICATION_JSON',
                        responseHandle: 'NONE',
                        timeout: 60,
                        validResponseCodes: '200',
                        ignoreSslErrors: true,
                    )

                    // Capture the response status code and content
                    def SecondstatusCode = res.getStatus()
                    def SecondresponseBody = res.getContent()

                    echo "Response Status Code: ${SecondstatusCode}"
                    echo "Response Body: ${SecondresponseBody}"

                    // You can now process or parse the response as needed
                    // For example, parsing JSON:
                    def jsonResponseSecond= new groovy.json.JsonSlurper().parseText(SecondresponseBody)
                    echo "Parsed JSON Response: ${jsonResponseSecond}"
                    
                }
            }
        }
    }
}
