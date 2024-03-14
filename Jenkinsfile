pipeline {
    agent any
    triggers {
        cron('H/10 * * * 4') // Triggers every 10 minutes on Thursdays
    }
    stages {
        stage('Build') {
            steps {
                script {
                    // Building project (assuming Maven)
                    sh 'mvn clean package'
                }
            }
        }
        stage('Test and Generate JaCoCo Report') {
            steps {
                script {
                    // Running tests and generating JaCoCo coverage report
                    sh 'mvn test jacoco:report'
                }
            }
        }
        // Add other stages like 'Deploy' as needed
    }
    post {
        always {
            // Archive the JaCoCo reports
            jacoco(execPattern: '**/*/target/site/jacoco/jacoco.xml')
        }
    }
}
