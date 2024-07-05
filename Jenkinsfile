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
            when {
                allOf {
                    branch 'main'
                    expression { env.TAG_NAME != env.BRANCH_NAME }
                }
            }
            steps {
                script {
                    // sh 'sonar-scanner -Dsonar.host.url=https://sonar.chaitu.net -Dsonar.login=admin -Dsonar.password=@123Chaitu -Dsonar.projectKey=backend -Dsonar.qualitygate.wait=true'
                    echo 'code Quality'
                }
            }
        }

        stage('Unit Tests') {
            when {
                allOf {
                    branch 'main'
                    expression { env.TAG_NAME != env.BRANCH_NAME }
                }
            }
            steps {
                echo 'Run your unit tests here'
            }
        }

        stage('Release') {
            when {
                expression { env.TAG_NAME ==~ ".*" } // any tag name it should be run
            }
            steps {
                sh 'zip -r backend-${TAG_NAME}.zip node_modules schema DbConfig.js package.json index.js TransactionService.js'
                //sh 'curl  -L -v -u admin:@123Chaitu --upload-file backend-${TAG_NAME}.zip  https://nexus.chaitu.net/repository/backend/backend-${TAG_NAME}.zip'
                sh 'curl -sSf -u "admin:@123Chaitu" -X PUT -T backend-${TAG_NAME}.zip "https://nexus.chaitu.net/repository/backend/backend-${TAG_NAME}.zip"'
            }
        }
    }
}
