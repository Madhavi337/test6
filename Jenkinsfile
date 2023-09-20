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
                        Authorization: 'Bearer eyJraWQiOiIzNjI3Zjc2MC1hOWQ5LTRmMDEtOTBiMS01NDU1NjE5MjczNDkiLCJhbGciOiJSUzI1NiJ9.eyJzdWIiOiJhZG1pbiIsInNjb3BlIjoiZGVmYXVsdCIsImlzcyI6Imh0dHBzOlwvXC8wOjA6MDowOjA6MDowOjE6OTE2NFwvIiwiZXhwIjoxNjk1MTgyMTQyfQ.r4nKG9nFTmOOwKghbyYGsFRvNx561RzOlwgc5DXAToppcz5VYNM64wbqvno8m3OmftEuphnRm06mGMkKRQZJTPp6H9RrGkGKuaaHB09_T3l6VVRZJsNK7CAtT6LmegLZVxIlR99Fad_lcqpI1ZB2Ev4aFwn5HuE1I_qEwBeUKxpQfLhCu91snpG_j8mjqBw3dtoHKAMGboFpd7L2dB4le0TewdZl5lP5tsLcj1BqNs4oV7hQOnfqnITAYBJpZT3_HH9gsKHLBZ9u_iAgSnVfct2Q5cRHfv9r1fbULhsTZ8A3cZoUqZ1JMcVRYXf_tmotUbXXawO4Oxd74r5S8wboRg',
                        responseHandle: 'NONE', // Use 'NONE' to capture the raw response
                        timeout: 60, // Set the timeout in seconds
                        validResponseCodes: '200', // Define the expected response code(s)
                        ignoreSslErrors: true// Set to true if the endpoint uses self-signed SSL certificates
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