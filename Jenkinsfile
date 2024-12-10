pipeline {
    agent any
    environment {
        SONARQUBE_SERVER = 'sonarserver' // Jenkins SonarQube configuration
        NEXUS_URL = 'http://13.235.95.61:8081/'
        NEXUS_CREDENTIALS_ID = 'NexusLogins'
        DOCKER_HUB_CREDENTIALS = 'dockerid'
        DOCKER_IMAGE = 'vishnusoman85/react-app'
        DOCKER_TAG = "1.0.${BUILD_NUMBER}"
    }
    stages {
        stage('Checkout Code') {
            steps {

                git branch: 'master', credentialsId: 'githubpass', url: 'https://github.com/Beerus-cmd/docker-reactjs.git'
        
            }
        }

        stage('Code Analysis with SonarQube') {
            steps {
                withSonarQubeEnv('sonarserver') {
                    sh 'npm install'
                    sh 'npx sonarscanner'
                }
            }
        }

        stage('Run Tests') {
            steps {
                sh 'npm test'
            }
        }
    }
}

