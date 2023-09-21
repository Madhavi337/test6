pipeline {
    agent any
    stages {
        stage('Call Endpoint') {
            steps {
                script {

                    
                    
                    def response = httpRequest(
                        url: 'https://localhost:9164/management/login',
                        httpMode: 'GET', // Use GET, POST, or other HTTP methods as needed
                        customHeaders:[[name:"Authorization",value:"Basic YWRtaW46YWRtaW4="]],
                        acceptType: 'APPLICATION_JSON',
                        responseHandle: 'NONE', // Use 'NONE' to capture the raw response
                        timeout: 60, // Set the timeout in seconds
                        validResponseCodes: '200', // Define the expected response code(s)
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
                    echo "Parsed JSON Token"


                    // Parse the JSON to extract the access token
// Your JSON string
                    def jsonResp = '''
                    {
                        "AccessToken": "eyJraWQiOiIzMjg0ZGNiYS0zYTFiLTRhNjUtYTkwYS1kODM4YzMzMDkxYzIiLCJhbGciOiJSUzI1NiJ9.eyJzdWIiOiJhZG1pbiIsInNjb3BlIjoiZGVmYXVsdCIsImlzcyI6Imh0dHBzOlwvXC8wOjA6MDowOjA6MDowOjE6OTE2NFwvIiwiZXhwIjoxNjk1MjY2NzE4fQ.YCPnKEi-pe9GKbRS7VA5wMCVGIQM6df0Rl9PuKKBky7Q4k20nd4hswDl_AFz9F66EkWc8TDbxHAhlgD50_TMw7z6cpFiGleP5FS9slt4ZwK7TvwA2nFUXJQ14DEJYPW4Don4EhhuLPLgwdR36IIxq5le7X0S--52huT3dHiUGkUINISI9HxxxY6z73kjC0wSOhCjF3CsDBUGliFDA8Hfz_dEv9XOwASl_THZHH95lTAVr04nwvhaTmlnl8tjK-YSY3yfKF6vSkSMYGbRJnMJP_nwsUh33WFkHio67Uh8ARwcThRofYMKpqgIziMbzeDbN30PhzSRLNzc7DJjyEE9Wg"
                    }
                    '''

                    def accessToken = readJSON text: jsonResp

                    def accessTokenValue = accessToken.AccessToken

                    echo "Access Token: ${accessTokenValue}"

                    // Parse the JSON to extract the access token
                    //def accessToken = sh(script: "echo '${json}' | jq -r '.AccessToken'", returnStdout: true).trim()

                    //echo "Access Token: ${accessToken}"



                    // Check the HTTP response status
                    if (response.status == 200) {
                        echo "API call was successful. ResponseBody: ${responseBody}"
                       

                    // Now, you can use 'accessToken' in subsequent steps
                        echo "Access token Successfull"
                    
                    } else {
                        error "API call failed with status.Response Status Code: ${statusCode}."
                    }
                    
                
                }
            }
        }
    }

}