pipeline {
    agent any

    stages {

        stage('Init') {
            steps {
                bat 'mvn clean'
            }
        }

        stage('Test') {
            steps {
                junit testResults: 'target/surefire-reports/*.xml',
                      allowEmptyResults: true
            }
        }

        stage('Build') {
            steps {
                bat 'mvn package'
                archiveArtifacts artifacts: 'target/*.jar', allowEmptyArchive: true
            }
            post {
                success {
                    echo "✅ Build success"
                }
                failure {
                    echo "❌ Build failure"
                }
            }
        }

        stage('Publish Report') {
            steps {
                publishHTML(target: [
                    allowMissing: false,
                    alwaysLinkToLastBuild: true,
                    keepAll: true,
                    reportDir: 'target/site/apidocs',
                    reportFiles: 'index.html',
                    reportName: 'My Reports',
                    reportTitles: 'The Report'
                ])
            }
        }
    }

    post {
        success {
            echo "🎉 PIPELINE SUCCESS"
        }
        failure {
            echo "🔥 PIPELINE FAILED"
        }
    }
}
