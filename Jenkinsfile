pipeline {
    agent any

    environment {
        inputdata = '' // Define inputdata at the pipeline level
    }

    stages {
        stage('Call First Endpoint') {
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


                    if (statusCode == 200) {
                        // You can now process or parse the response as needed
                    // For example, parsing JSON:

                        def jsonResponseFirst = new groovy.json.JsonSlurper().parseText(responseBody)
                        echo "Parsed JSON Response First: ${jsonResponseFirst}"
                        inputdata = jsonResponseFirst.AccessToken // Assign inputdata at the pipeline level
                        echo "AccessTokenFirst: ${inputdata}"
                    }
                    
                }
            }
        }
        stage('Call Second Endpoint') { // Give it a unique name
            steps {
                script {
                    echo "AccessTokenFirst: ${inputdata}"
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
                    def jsonResponseSecond = new groovy.json.JsonSlurper().parseText(SecondresponseBody)
                    echo "Parsed JSON Response Second: ${jsonResponseSecond}"
                    
                }
            }
        }
    }
}
