pipeline {
    agent any
    tools {
        maven 'MonMaven' // On utilise l'outil configuré au TP2
    }
    stages {
        stage('Nettoyage & Préparation') {
            steps {
                echo 'Nettoyage de l\'espace de travail...'
                sh 'mvn clean'
            }
        }
        stage('Compilation') {
            steps {
                echo 'Compilation de l\'application...'
                sh 'mvn compile'
            }
        }
        stage('Tests Unitaires') {
            steps {
                echo 'Exécution des tests unitaires...'
                sh 'mvn test'
            }
        }
    }
}
