pipeline {
    agent any
    environment {
        DOCKER_IMAGE = 'flask-app:latest'
        SONARQUBE_URL = 'http://localhost:9000'
        SELENIUM_GRID_URL = 'http://localhost:4444/wd/hub'
        SONAR_SCANNER_HOME = '/opt/sonar-scanner' // Assuming SonarQube Scanner is installed here
        PATH = "${SONAR_SCANNER_HOME}/bin:${env.PATH}"
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
                     sh "sonar-scanner --version"
                }
                
            }
      }

    }
}

def seleniumTests() {
     echo "hello tests" 
}
