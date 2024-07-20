pipeline {
    agent any

    environment {
        NVD_API_KEY = '13660f4c-e4d7-45eb-a354-0558339cdc4e'
    }

    stages {
        stage('OWASP DependencyCheck') {
            steps {
                dependencyCheck additionalArguments: '--format HTML --format XML --nvdApiKey ${NVD_API_KEY}', odcInstallation: 'OWASP Dependency-Check Vulnerabilities'
            }
        }
    }

    post {
        success {
            dependencyCheckPublisher pattern: 'dependency-check-report.xml'
        }
    }
}
