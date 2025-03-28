pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/Disha647/task6.2C-jenkins.git'
            }
        }

        stage('Build') {
            steps {
                echo 'Building the application... npm and Maven can be used for Building...'
                bat 'echo Build step running on Windows'
                // Replace this with your actual build command, e.g.,
                // bat 'mvn clean install' (for Maven)
                // bat 'npm install && npm run build' (for Node.js)
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                bat 'echo Running unit and integration tests...'
                // Replace with actual test command, e.g., bat 'mvn test'
            }
        }

        stage('Code Analysis') {
            steps {
                bat 'echo Performing code analysis...'
                // Add relevant analysis commands here
            }
        }

        stage('Security Scan') {
            steps {
                bat 'echo Running security scans...'
                // Add security scan commands
            }
        }

        stage('Deploy to Staging') {
            steps {
                bat 'echo Deploying to staging environment...'
                // Add deployment steps here
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                bat 'echo Running integration tests on staging...'
                // Add integration test steps
            }
        }

        stage('Deploy to Production') {
            steps {
                bat 'echo Deploying to production environment...'
                // Add production deployment steps
            }
        }
    }

    post {
        always {
            echo 'Pipeline execution completed.'
            emailext(
                to: 'disha.chawla6025@gmail.com',
                subject: 'Jenkins Build Notification',
                body: 'The Jenkins build has completed. Check the pipeline for details.'
            )
        }
    }
}
