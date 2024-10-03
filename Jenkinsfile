pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'Building the project...'
                // Use Maven to build the code
                // e.g., sh 'mvn clean package'
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                echo 'Running Unit and Integration tests...'
                // Use JUnit for unit tests
                // e.g.., junit 'target/surefire-reports/*.xml'
                // Use Selenium for integration tests
            }
        }
        stage('Code Analysis') {
            steps {
                echo 'Performing Code Analysis...'
                // Use SonarQube to analyze the code quality
                // e.g., sh 'mvn sonar:sonar'
            }
        }
        stage('Security Scan') {
            steps {
                echo 'Running Security Scan...'
                // Use a tool like OWASP Dependency-Check or Snyk for security scanning
                // e.g., sh 'dependency-check.sh'
            }
        }
        stage('Deploy to Staging') {
            steps {
                echo 'Deploying to Staging...'
                // Deploy to an AWS EC2 instance or another staging server
                // e.g., using SSH to deploy
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                echo 'Running Integration Tests on Staging...'
                // Run end-to-end tests in staging
                // e.g., using Selenium WebDriver or Postman
            }
        }
        stage('Deploy to Production') {
            steps {
                echo 'Deploying to Production...'
                // Deploy to production server, e.g., another EC2 instance
            }
        }
    }
  post {
        success {
            // Send an email with logs when the build is successful
            emailext(
                subject: "Jenkins Build Success: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                body: "Build was succesful"
                {env.BUILD_NUMBER} of job ${env.JOB_NAME} has succeeded.
              
                View details at: ${env.BUILD_URL}
                """,
                recipientProviders: [[$class: 'DevelopersRecipientProvider']],
                attachLog: true // Attaches the build log
                to: 'jkat.rk@gmail.com'
            )
        }
        failure {
            mail bcc: '', 
                 body: '''. Unfortunately, the build has failed.
Check the details at ${env.BUILD_URL}.''', 
                 cc: '', 
                 from: 'your-email@example.com',  // Replace with your email
                 replyTo: '', 
                 subject: 'Jenkins Build Notification - Failure', 
                 to: 'jkat.rk@gmail.com'
        }
    }
}
