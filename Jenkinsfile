pipeline {
    agent any // Use any available agent

    // Trigger the build every 10 minutes on Mondays
    triggers {
        cron('H/10 * * * 1')
    }

    stages {
        stage('Build') {
            steps {
                script {
                    // Use bat instead of sh for Windows
                    bat 'mvn clean package'
                }
            }
        }

        stage('Code Coverage') {
            steps {
                script {
                    // Use bat instead of sh for Windows
                    bat 'mvn test jacoco:report'
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
