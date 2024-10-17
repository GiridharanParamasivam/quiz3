pipeline {
    agent any 
    triggers {
        cron('H/10 * * * 1') // Trigger every 10 minutes on Mondays
    }
    stages {
        stage('Build') {
            steps {
                script {
                    // Run Gradle build
                    sh './gradlew build'
                }
            }
        }
        stage('Code Coverage') {
            steps {
                script {
                    // Run tests and generate Jacoco report
                    sh './gradlew test jacocoTestReport'
                }
            }
        }
    }
    post {
        always {
            // Archive the Jacoco report
            archiveArtifacts artifacts: 'build/reports/jacoco/test/html/*.html', fingerprint: true
        }
    }
}
