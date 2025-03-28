pipeline {
    agent any

    environment {
        EMAIL = 'disha.chawla6025@gmail.com'
    }

    stages {
        stage('Build') {
            steps {
                echo 'Building the application... npm and Maven can be used for Building...'
                sh 'npm install && npm run build'  // If using Node.js
                sh 'mvn clean package'  // If using Java
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                echo 'Running unit and integration tests... JUnit can be used for testing.'
                sh 'mvn test'  // If using JUnit for Java
            }
            post {
                success {
                    emailext(
                        subject: "Unit Tests Passed",
                        body: "Unit tests completed successfully!!!",
                        to: "${EMAIL}"
                    )
                }
                failure {
                    emailext(
                        subject: "Unit Tests Failed",
                        body: "Unit tests failed. Check Jenkins logs.",
                        to: "${EMAIL}"
                    )
                }
                always {
                    emailext(
                        subject: "Build Completed: ${env.JOB_NAME} - Build #${env.BUILD_NUMBER}",
                        body: "Check console output at ${env.BUILD_URL} to view the results.",
                        to: "${EMAIL}"
                    )
                }
            }
        }

        stage('Code Analysis') {
            steps {
                echo 'Performing code analysis... SonarQube can be used for code analysis.'
                sh 'mvn sonar:sonar'  // Replace with actual SonarQube command
            }
        }

        stage('Security Scan') {
            steps {
                echo 'Performing security scan... OWASP Dependency-Check can be used for security scan.'
                sh 'dependency-check --project myProject --scan .'  // Replace with security scan command
            }
            post {
                success {
                    emailext(
                        subject: "Security Scan Passed",
                        body: "Security scan completed successfully.",
                        to: "${EMAIL}"
                    )
                }
                failure {
                    emailext(
                        subject: "Security Scan Failed",
                        body: "Security vulnerabilities found. Check Jenkins logs.",
                        to: "${EMAIL}"
                    )
                }
            }
        }

        stage('Deploy to Staging') {
            steps {
                echo 'Deploying to staging environment... AWS, Docker can be used in Deployment.'
                sh './deploy_to_staging.sh'  // Replace with actual deployment script
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                echo 'Running integration tests on staging... Cypress can be used for integration tests.'
                sh 'npx cypress run'  // If using Cypress
            }
        }

        stage('Deploy to Production') {
            steps {
                echo 'Deploying to production environment... Heroku could be used for this deployment.'
                sh 'heroku login && git push heroku main'  // Replace with actual Heroku deployment command
            }
        }
    }

    post {
        always {
            echo 'Pipeline execution completed.'
            emailext(
                subject: "Pipeline Execution Completed",
                body: "The Jenkins pipeline has finished execution.",
                to: "${EMAIL}"
            )
        }
    }
}
