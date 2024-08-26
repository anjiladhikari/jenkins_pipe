pipeline {
    agent any

    environment {
        RECIPIENT_EMAIL = 'anjiladlee10@gmail.com'  
    }

    stages {
        stage('Build') {
            steps {
                echo 'Building the code using Maven...'
                // Tool: Maven reference https://www.jenkins.io/doc/tutorials/build-a-java-app-with-maven/
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                echo 'Running unit tests with JUnit...'
                echo 'Running integration tests with JUnit...'
                // Tool: JUnit reference https://www.educba.com/junit-integration-test/
            }
        }

        stage('Code Analysis') {
            steps {
                echo 'Analyzing code quality with SonarQube...'
                // Tool: SonarQube reference https://thectoclub.com/tools/best-code-analysis-tools/
            }
        }

        stage('Security Scan') {
            steps {
                echo 'Performing security scan with OWASP Dependency Check...'
                // Tool: OWASP Dependency Check reference https://medium.com/@vaibhavverma016/automated-security-testing-with-jenkins-and-owasp-zap-step-by-step-guide-e2c1bce2f039
            }
        }

        stage('Deploy to Staging') {
            steps {
                echo 'Deploying to staging environment on AWS EC2...'
                // Tool: AWS CLI reference  https://wpmudev.com/blog/testing-staging-environment-tools/
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                echo 'Running integration tests on staging environment with JUnit...'
                // Tool: JUnit or others
            }
        }

        stage('Deploy to Production') {
            steps {
                echo 'Deploying to production environment on AWS EC2...'
                // Tool: AWS CLI same as staging
            }
        }
    }

    post {
        always {
            script {
                def status = currentBuild.result ?: 'SUCCESS'
                emailext (
                    to: "${env.RECIPIENT_EMAIL}",
                    subject: "Jenkins Pipeline: ${status} Build",
                    body: "The build ${status.toLowerCase()}.",
                    attachLog: true
                )
            }
        }
    }
}
