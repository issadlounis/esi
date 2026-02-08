pipeline {
    agent any

    stages {

        stage('Init') {
            steps {
                // Nettoyer le projet
                bat 'mvn clean'
            }
        }



        stage('Test') {
            steps {
                
               junit 'target/surefire-reports/*.xml'

            }
        }
        stage('Build') {
            steps {
              
                bat 'mvn package'

                // Archive les fichiers JAR générés
                archiveArtifacts : 'target/*.jar'
            }
        }

       
        stage('documotation') {
            steps {
               bat: 'mvnw javadoc :javadoc'
            }
        }

    }
}
