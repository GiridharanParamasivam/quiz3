pipeline {
    agent any 
    triggers {
        cron('H/10 * * * 1') // Trigger every 10 minutes on Mondays
    }
    stages {
        stage('Build') {
            steps {
                script {
                    // Run Maven build
                    bat 'mvn clean package' // Use 'bat' for Windows
                }
            }
        }
        stage('Code Coverage') {
            steps {
                script {
                    // Run tests and generate Jacoco report
                    bat 'mvn test jacoco:report' // Use 'bat' for Windows
                }
            }
        }
    }
    post {
        always {
            // Archive the Jacoco report
            archiveArtifacts artifacts: 'target/site/jacoco/*.html', fingerprint: true
        }
    }
}
