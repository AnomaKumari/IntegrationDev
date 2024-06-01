pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building the code using Maven...'
                // Example command to build using Maven
                // sh 'mvn clean package'
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                echo 'Running unit and integration tests using JUnit and Selenium...'
                // Example command to run tests using Maven
                // sh 'mvn test'
            }
        }
        stage('Code Analysis') {
            steps {
                echo 'Performing code analysis using SonarQube...'
                // Example command to run SonarQube scanner
                // sh 'sonar-scanner'
            }
        }
        stage('Security Scan') {
            steps {
                echo 'Performing security scan using OWASP ZAP...'
                // Example command to run OWASP ZAP
                // sh 'zap-cli scan'
            }
        }
        stage('Deploy to Staging') {
            steps {
                echo 'Deploying to staging server using AWS CLI...'
                // Example command to deploy to AWS EC2
                // sh 'aws deploy create-deployment --application-name <app-name> --deployment-group-name <group-name> --s3-location bucket=<bucket-name>,bundleType=zip,key=<key>'
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                echo 'Running integration tests on staging using Selenium...'
                // Example command to run integration tests on staging
                // sh 'mvn verify -Pstaging'
            }
        }
        stage('Deploy to Production') {
            steps {
                echo 'Deploying to production server using AWS CLI...'
                // Example command to deploy to AWS EC2
                // sh 'aws deploy create-deployment --application-name <app-name> --deployment-group-name <group-name> --s3-location bucket=<bucket-name>,bundleType=zip,key=<key>'
            }
        }
    }

    post {
        always {
            script {
                emailext(
                    to: 'codmobiledev@gmail.com',
                    subject: "Pipeline ${currentBuild.currentResult}: ${env.JOB_NAME} ${env.BUILD_NUMBER}",
                    body: """
                    Build Status: ${currentBuild.currentResult}
                    Job: ${env.JOB_NAME} 
                    Build Number: ${env.BUILD_NUMBER}
                    Check console output at ${env.BUILD_URL}
                    """,
                    attachLog: true
                )
            }
        }
    }
}
