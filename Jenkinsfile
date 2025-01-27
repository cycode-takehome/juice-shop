pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'Building the project...'
            }
        }
        stage('Cycode Scan') {
            steps {
                script {
                    def response = httpRequest(
                        httpMode: 'POST',
                        url: 'http://cycode-broker-client:9494/healthy',
                        contentType: 'APPLICATION_JSON',
                        requestBody: """
                        {
                            "repository": "https://github.com/cycode-takehome/juice-shop",
                            "branch": "master"
                        }
                        """
                    )
                    echo "Response from Cycode Broker: ${response.content}"
                }
            }
        }
    }
}
