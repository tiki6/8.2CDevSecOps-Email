pipeline {
    agent any

    tools {
        nodejs 'NodeJS'
    }

    stages {

        stage('Install Dependencies') {
            steps {
                echo 'Installing dependencies using npm.'
                bat 'npm install'
            }
        }

        stage('Run npm Audit') {
            steps {
                echo 'Running npm audit security test.'
                bat 'npm audit || exit 0'
            }

            post {
                always {
                    emailext(
                        subject: 'Security Scan Completed',
                        body: 'The npm audit stage has completed. Build logs are attached.',
                        to: 'talhaibnehasan@gmail.com',
                        attachLog: true
                    )
                }
            }
        }

        stage('Run npm Test') {
            steps {
                echo 'Running npm test.'
                bat 'npm test || exit 0'
            }

            post {
                always {
                    emailext(
                        subject: 'npm Test Completed',
                        body: 'The npm test stage has completed. Build logs are attached.',
                        to: 'talhaibnehasan@gmail.com',
                        attachLog: true
                    )
                }
            }
        }
    }

    post {
        always {
            echo 'Pipeline with email notification completed.'
        }
    }
}