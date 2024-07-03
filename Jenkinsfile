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
                    branch 'main'
            }
            steps {
                echo 'Run your unit tests here'
                // Example: sh 'npm test'
            }
        }

        stage('Release') {
            when {
                expression { env.TAG_NAME ==~ ".*" } // any tag name it should be run
            }
            steps {
                echo 'Perform release steps here'
                // Example: sh 'npm publish'
            }
        }
    }
}
