pipeline {
    agent { label 'workstation' }

    stages {
        stage('Download dependencies'){
            steps {
                sh 'npm install'
            }
        }

        stage('Code Quality'){
            steps {
                sh 'sonar-scanner -Dsonar.host.url=https://sonar.chaitu.net -Dsonar.login=admin -Dsonar.password=@123Chaitu -Dsonar.projectKey=backend -Dsonar.qualitygate.wait=true'
            }
        }

        stage('Unit Tests'){
            steps {
                echo 'ci'
            }

        stage('Release'){
            steps {
                echo 'ci'
            }
        }
    }
}
