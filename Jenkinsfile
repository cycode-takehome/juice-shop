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
                        url: 'http://localhost:9494/api/v1/scan',
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
