pipeline {
    agent any
    environment {
        DOCKER_IMAGE = 'flask-app:latest'
        SONARQUBE_URL = 'http://localhost:9000'
        SONARQUBE_SCANNER = 'SonarQubeScanner'
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
    }
}
