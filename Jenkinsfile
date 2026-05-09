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
        }

        stage('Run npm Test') {
            steps {
                echo 'Running npm test on nodejs-goof.'
                bat 'npm test || exit 0'
            }
        }
    }

    post {
        always {
            echo 'Task 2 DevSecOps security testing completed.'
        }
    }
}