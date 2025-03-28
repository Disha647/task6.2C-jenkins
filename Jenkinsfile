pipeline {
    agent any
    environment {
        RECIPIENT_EMAIL = 'disha.chawla6025@gmail.com'
    }

    stages {
        stage('Compile & Build') {
            steps {
                echo 'Initializing build process... Utilizing npm and Maven where necessary.'
            }
        }

        stage('Testing: Unit & Integration') {
            steps {
                echo 'Executing unit and integration tests... JUnit is an option for testing.'
            }
            post {
                success {
                    emailext(
                        subject: "Unit Tests Successful",
                        body: "All unit tests passed successfully! 🎉",
                        to: "${RECIPIENT_EMAIL}"
                    )
                }
                failure {
                    emailext(
                        subject: "Unit Tests Failed",
                        body: "Unit tests encountered errors. Review the Jenkins logs for details.",
                        to: "${RECIPIENT_EMAIL}"
                    )
                }
                always {
                    emailext(
                        subject: "Build Report: ${env.JOB_NAME} - #${env.BUILD_NUMBER}",
                        body: "Check the full output at: ${env.BUILD_URL}",
                        to: 'disha.chawla6025@gmail.com'
                    )
                }
            }
        }

        stage('Static Code Review') {
            steps {
                echo 'Running static analysis... ESLint can assist with code quality checks.'
            }
        }

        stage('Security Audit') {
            steps {
                echo 'Performing security assessment... Bandit can assist in scanning vulnerabilities.'
            }
            post {
                success {
                    emailext(
                        subject: "Security Scan Passed",
                        body: "No security threats detected. All checks passed.",
                        to: "${RECIPIENT_EMAIL}"
                    )
                }
                failure {
                    emailext(
                        subject: "⚠Security Scan Failed",
                        body: "Potential vulnerabilities detected. Review the logs for further investigation.",
                        to: "${RECIPIENT_EMAIL}"
                    )
                }
            }
        }

        stage('Staging Deployment') {
            steps {
                echo 'Deploying application to the staging environment... AWS and Docker may be utilized.'
            }
        }

        stage('Validation on Staging') {
            steps {
                echo 'Running integration tests on staging... Cypress is a possible tool for this.'
            }
        }

        stage('Production Rollout') {
            steps {
                echo 'Deploying the final build to production... Heroku could facilitate deployment.'
            }
        }
    }

    post {
        always {
            echo 'CI/CD pipeline execution finished.'
        }
    }
}
