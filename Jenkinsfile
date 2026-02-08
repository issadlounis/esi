pipeline {
    agent any

    stages {

        stage('Build') {
            steps {
                // Compile et package le projet Maven
                bat 'mvn clean package'
                
                // Archive les fichiers JAR générés
                archiveArtifacts artifacts: 'target/*.jar', allowEmptyArchive: true
            }
        }

        stage('Test') {
            steps {
                // Exécute les tests et publie les résultats JUnit
                junit 'target/surefire-reports/*.xml'
            }
        }
    }
}
