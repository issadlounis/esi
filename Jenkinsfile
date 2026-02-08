pipeline {
    agent any

    stages {

        stage('Init') {
            steps {
                // Nettoyer le projet
                bat 'mvn clean'
            }
        }

        stage('Build') {
            steps {
                // Compiler et packager le projet Maven
                bat 'mvn package'
                
                // Archive les fichiers JAR générés
                archiveArtifacts artifacts: 'target/*.jar', allowEmptyArchive: true
            }
        }

        stage('Test') {
            steps {
                // Exécute les tests et publie les résultats JUnit
                junit allowEmptyResults: true, testResults: 'target/surefire-reports/*.xml'
            }
        }

    }
}
