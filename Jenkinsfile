pipeline {
    agent any
    stages {
        stage('Call Endpoint') {
            steps {
                script {

                    def accessToken = 'eyJraWQiOiJiZTg2YTE3YS0zZDVkLTRiYTMtOTIxNy02MDdhZGM4NzdhNjgiLCJhbGciOiJSUzI1NiJ9.eyJzdWIiOiJhZG1pbiIsInNjb3BlIjoiZGVmYXVsdCIsImlzcyI6Imh0dHBzOlwvXC8wOjA6MDowOjA6MDowOjE6OTE2NFwvIiwiZXhwIjoxNjk1MTk0MDMzfQ.mL0obV-9xSDjtEfujAeLPMlRvsbp2iZ2PT3YE45izTgEGtJxdJ6Ebj7nJU5P6zZMncZf5lWtNhrGbjMWC8Le_3k4Ey5WkrwN_BwUst7nXZ3lrrgldvb6pWQ3sUWbS6reoYPj6o9quA9z5WCNGUMUgwhLEfSdskezDS_ISAqoY_Kh882vgRDqaZChAu96vQfGuOjAFsmQCpVY_Og2b5tvNIuw3XMBbWQQfKiLgI-E9l9J95kDDlOsTbbpFZjOtig6XP3IDz28LomZgIzz-1Ky1syebjBrbmczx5VRahNwrsmvnWJ0K9HGw2azGZzT5FeNK6KH9_Ew1VRwzzqlTvGV9g' // Replace with your actual Bearer token
                    // Define HTTP headers, including the Authorization header with the Bearer token

                    def headers = [
                        Authorization: 'Bearer ' + accessToken
                    ]
                    def response = httpRequest(
                        url: 'https://localhost:9164/management/applications',
                        httpMode: 'GET', // Use GET, POST, or other HTTP methods as needed
                        contentType: 'APPLICATION_JSON',
                        acceptType: 'APPLICATION_JSON',
                        responseHandle: 'NONE', // Use 'NONE' to capture the raw response
                        timeout: 60, // Set the timeout in seconds
                        ignoreSslErrors: true,// Set to true if the endpoint uses self-signed SSL certificates
                        Authorization: 'Bearer eyJraWQiOiIxY2ViNzdiMC1hMTU0LTRmNTktYTVjNS05ZjZhNzJmMGFkN2QiLCJhbGciOiJSUzI1NiJ9.eyJpc3MiOiJodHRwczpcL1wvMDowOjA6MDowOjA6MDoxOjkxNjRcLyIsInN1YiI6ImFkbWluIiwiZXhwIjoxNjk1MTI0NjI2LCJzY29wZSI6ImFkbWluIn0.idmZx5D24Ng3FtQaiXI608K1043abo_xFQLsyE0w3njz2OGbn78ncx59_zxnmpDU2xwyBMCKGWDsZf3-GB5kmJhCgjGdkJncivm18ZCAUhXguLE0JFOz8tfHh-LGR9UGIDLZ3vp-my0wZzLUAS_lQUJEcO0jSJ5c5-7-rH5TqZR9h1Zlw5qFnZCFpR9Yk0E_xA4NpUjcigabuNt4wbwyfevOpWTMaDlR6SowJ3f2A9x6sQt9HLW2E0BYIHfrTySZdCL8UkjVh-8svCH9ppE8OvjrV8wTRcNB2Llz5TCAlyWY9C-uX-qNbI3ALDUhHBcF7dMubmjXoWmRqrluJqEGxg'
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
                    
                    
                    // Check the HTTP response status
                    if (response.status == 200) {
                        echo "API call was successful. Response body: ${responseBody}"
                    } else {
                        error "API call failed with status ${statusCode}."
                    }
                }
            }
        }
    }

}