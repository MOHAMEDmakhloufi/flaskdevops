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
        
      stage("Run SonarQube Analysis") {
            steps {
                 script {
                     sh "java --version"
                }
                
            }
      }

    }
}

def seleniumTests() {
     echo "hello tests" 
}
