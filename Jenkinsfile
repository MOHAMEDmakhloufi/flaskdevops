pipeline {
    agent any
    environment {
        DOCKER_IMAGE = 'flask-app:latest'
        SONARQUBE_URL = 'http://localhost:9000'
        SELENIUM_GRID_URL = 'http://localhost:4444/wd/hub'
    }
    stages {
        stage("Init") {
            steps {
                script {
                    echo "Initial Configuration"
                }
            }
        }
        stage("Build Image") {
            steps {
                script {
                    sh "docker build -t $DOCKER_IMAGE ."
                }
            }
        }
      stage("Run SonarQube Analysis") {
            steps {
                withCredentials([string(credentialsId: 'sonarqube-token', variable: 'SONARQUBE_SCANNER')]) {
                    withSonarQubeEnv(installationName:'sonarQube') {
                        sh "sonar-scanner "
                    }
                }
            }
         stage("Run Tests") {
            steps {
                script {
                    // Run the Docker container for testing
                    def app = sh(script: "docker run -d -p 5000:5000 ${DOCKER_IMAGE}", returnStdout: true).trim()
                    try {
                        seleniumTests()
                    } finally {
                        // Stop the Docker container
                        sh "docker stop ${app}"
                        sh "docker rm ${app}"
                    }
                }
            }
        }
    }
}

def seleniumTests() {
     echo "hello tests" 
}
