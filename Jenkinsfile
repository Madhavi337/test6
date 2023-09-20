pipeline {
    agent any
    stages {
        stage('Call Endpoint') {
            steps {
                script {
                    def response = httpRequest(
                        url: 'https://localhost:9164/management/applications',
                        httpMode: 'GET', // Use GET, POST, or other HTTP methods as needed
                        contentType: 'APPLICATION_JSON',
                        acceptType: 'APPLICATION_JSON',
                        responseHandle: 'NONE', // Use 'NONE' to capture the raw response
                        timeout: 60, // Set the timeout in seconds
                        validResponseCodes: '200', // Define the expected response code(s)
                        ignoreSslErrors: true,// Set to true if the endpoint uses self-signed SSL certificates
                        customHeaders: [[name: 'Authorization', value: 'Bearer eyJraWQiOiIxY2ViNzdiMC1hMTU0LTRmNTktYTVjNS05ZjZhNzJmMGFkN2QiLCJhbGciOiJSUzI1NiJ9.eyJpc3MiOiJodHRwczpcL1wvMDowOjA6MDowOjA6MDoxOjkxNjRcLyIsInN1YiI6ImFkbWluIiwiZXhwIjoxNjk1MTI0NjI2LCJzY29wZSI6ImFkbWluIn0.idmZx5D24Ng3FtQaiXI608K1043abo_xFQLsyE0w3njz2OGbn78ncx59_zxnmpDU2xwyBMCKGWDsZf3-GB5kmJhCgjGdkJncivm18ZCAUhXguLE0JFOz8tfHh-LGR9UGIDLZ3vp-my0wZzLUAS_lQUJEcO0jSJ5c5-7-rH5TqZR9h1Zlw5qFnZCFpR9Yk0E_xA4NpUjcigabuNt4wbwyfevOpWTMaDlR6SowJ3f2A9x6sQt9HLW2E0BYIHfrTySZdCL8UkjVh-8svCH9ppE8OvjrV8wTRcNB2Llz5TCAlyWY9C-uX-qNbI3ALDUhHBcF7dMubmjXoWmRqrluJqEGxg']]
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