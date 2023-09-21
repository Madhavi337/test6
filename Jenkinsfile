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

                    // Process the response of the first endpoint
                    // Extract and use the access token as needed
                }
            }
        }
        stage('Call Second Endpoint') { // Give it a unique name
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

                    // Process the response of the first endpoint
                    // Extract and use the access token as needed
                }
            }
        }
    }
}
