pipeline {
    agent any
    stages {
        stage('Call Endpoint') {
            steps {
                script {
                    def response = httpRequest(
                        url: 'https://localhost:9164/management/login',
                        httpMode: 'GET',
                        customHeaders:[[name:"Authorization",value:"Basic YWRtaW46YWRtaW4="]],
                        acceptType: 'APPLICATION_JSON',
                        responseHandle: 'NONE',
                        timeout: 60,
                        validResponseCodes: '200',
                        ignoreSslErrors: true,
                    )

                    def statusCode = response.getStatus()
                    def responseBody = response.getContent()

                    echo "Response Status Code: ${statusCode}"
                    echo "Response Body: ${responseBody}"

                    if (statusCode == 200) {
                        def jsonResponse = new groovy.json.JsonSlurper().parseText(responseBody)
                        def accessTokenValue = jsonResponse.AccessToken
                        echo "AccessToken: ${accessTokenValue}"

                        def res = httpRequest(
                            url: 'https://localhost:9164/management/applications',
                            httpMode: 'GET',
                            customHeaders:[[name:"Authorization",value:"Bearer ${accessTokenValue}"]],
                            acceptType: 'APPLICATION_JSON',
                            responseHandle: 'NONE',
                            timeout: 60,
                            validResponseCodes: '200',
                            ignoreSslErrors: true,
                        )

                        // Capture the response status code and content for the second request
                        def statusCodeofSeondEP = res.getStatus()
                        def responseBodyofSeondEP = res.getContent()

                        echo "Response Status Code Second EP: ${statusCodeofSeondEP}"
                        echo "Response Body of Second EP: ${responseBodyofSeondEP}"

                        if (statusCode2 != 200) {
                            error "API call to the second endpoint failed with status: ${statusCodeofSeondEP}."
                        }
                    } else {
                        echo "API call to the first endpoint failed with status: ${statusCode}."
                    }
                }
            }
        }
    }
}
