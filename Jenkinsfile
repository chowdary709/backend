pipeline {
    agent {
        label 'workstation'
    }
    options {
        ansiColor('xterm')
    }

    stages {
        stage('Download dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Code Quality') {
            steps {
                script {
                    sh 'sonar-scanner -Dsonar.host.url=https://sonar.chaitu.net -Dsonar.login=admin -Dsonar.password=@123Chaitu -Dsonar.projectKey=backend -Dsonar.qualitygate.wait=true'
                }
            }
        }

        stage('Unit Tests') {
            steps {
                echo 'Run your unit tests here'
                // Example: sh 'npm test'
            }
        }

        stage('Release') {
            steps {
                echo 'Perform release steps here'
                // Example: sh 'npm publish'
            }
        }
    }
}
