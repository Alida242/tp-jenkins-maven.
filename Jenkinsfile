pipeline {
    agent any
    tools {
        maven 'MonMaven' // On utilise l'outil configuré au TP2
    }
    stages {
        stage('Nettoyage & Préparation') {
            steps {
                echo 'Nettoyage de l\'espace de travail...'
                bat 'mvn clean'
            }
        }
        stage('Compilation') {
            steps {
                echo 'Compilation de l\'application...'
                bat 'mvn compile'
            }
        }
        stage('Tests Unitaires') {
            steps {
                echo 'Exécution des tests unitaires...'
                bat 'mvn test'
            }
        }
        stage('SonarQube Analysis') {
            steps {
                echo 'Analyse de la qualité du code avec SonarQube...'
                withSonarQubeEnv('SonarQube') {
                    bat 'mvn sonar:sonar'
                }
            }
        }
    }
}
