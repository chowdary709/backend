pipeline {
    agent { label 'workstation' }

    stages {
        stage('Download dependencies'){
            steps {
                sh 'npn install'
            }
        }

        stage('Code Quality'){
            steps {
                sh 'sonar-scanner -Dsonar.host.url=http://172.31.34.243:9000 -Dsonar.login=admin -Dsonar.password=admin123 -Dsonar.projectKey=backend -Dsonar.qualitygate.wait=true'
            }
        }

        stage('Release'){
            steps {
                echo 'ci'
            }
        }
    }
}
