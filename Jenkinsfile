pipeline {
    agent any
    environment {
        DOCKER_IMAGE = 'flask-app:latest'
        SONARQUBE_URL = 'http://192.168.1.21:9000/'
        SELENIUM_GRID_URL = 'http://localhost:4444/wd/hub'
        SONAR_SCANNER_HOME = '/opt/sonar-scanner' // Assuming SonarQube Scanner is installed here
        PATH = "${SONAR_SCANNER_HOME}/bin:${env.PATH}"
    }
    stages {
        stage("Init") {
            steps {
                script {
                    sh "ls"
                }
            }
        }
        
      stage("Run SonarQube Analysis") {
            steps {
                withCredentials([string(credentialsId: 'sonarqube-token', variable: 'SONARQUBE_SCANNER')]) {
                    withSonarQubeEnv(installationName:'sonarQube') {
                        sh '''
                            docker run --rm \
                            -e SONAR_HOST_URL=${SONARQUBE_URL} \
                            -e SONAR_LOGIN=${SONARQUBE_SCANNER} \
                            -v $(pwd):/usr/src \
                            sonarsource/sonar-scanner-cli \
                            sonar-scanner \
                            -Dsonar.projectKey=your-project-key \
                            -Dsonar.host.url=${SONARQUBE_URL} \
                            -Dsonar.login=${SONARQUBE_SCANNER}
                        '''
                    }
                }
            }
      }

    }
}

def seleniumTests() {
     echo "hello tests" 
}
