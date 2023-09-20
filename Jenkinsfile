pipeline {
    agent any
    stages {
        stage('Call Endpoint') {
            steps {
                script {

                    
                    
                    def response = httpRequest(
                        url: 'https://localhost:9164/management/applications',
                        httpMode: 'GET', // Use GET, POST, or other HTTP methods as needed
                        customHeaders:[[name:"Authorization",value:"eyJraWQiOiI4MWU3ZDAyNC1iZmRhLTQ2MDYtYTE1Yy1iNTE4ZjQ3ZTc3MGUiLCJhbGciOiJSUzI1NiJ9.eyJzdWIiOiJhZG1pbiIsInNjb3BlIjoiZGVmYXVsdCIsImlzcyI6Imh0dHBzOlwvXC8xMjcuMC4wLjE6OTE2NFwvIiwiZXhwIjoxNjk1MjExNTA2fQ.Al2a2wxFNOY8qXo19_3pBpxQXqr3ByLZodiQ-KTdDdTP0II-ARezY52-sgDRG-XOfW_SFcHM2TFhTkEg9TzhLpFhXyj4ifq865Y3-RFaMcnjHw_MGPChYpm0_oEqWYfwJU32GgRS1p2XUur-iH7qZOnSaHmWdv4UNzvr7qC-nHyBtISFVTSFm4N4i4LK5hjmmuwWVQbqnkHOFXOKq2kWbMuYCJqyHZpkvrQsvC2AcmNpd1A_4Ef27eqmnFhn33Y306Put7I_e0T3__I05Wc1E1EWU2GyBapo8ejCQy-V-suExhncSOOn1-HQTTCGN92pSGhvcL7u6n49-Qo9hBUueQ"]],
                        acceptType: 'APPLICATION_JSON',
                        responseHandle: 'NONE', // Use 'NONE' to capture the raw response
                        timeout: 60, // Set the timeout in seconds
                        ignoreSslErrors: true,// Set to true if the endpoint uses self-signed SSL certificates
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
                    
                    
                
                }
            }
        }
    }

}