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
         stage('Run Tests') {
            steps {
                script {
                    def app = docker.run(DOCKER_IMAGE, '-d -p 5000:5000')
                    app.stop()
                }
            }
        }
    }
}


