pipeline {
    agent any
    
    parameters {
        choice(name: 'ENVIRONNEMENT', choices: ['dev', 'recette', 'prod'], description: 'Sélectionnez l\'environnement de déploiement')
        string(name: 'VERSION', defaultValue: '1.0.0', description: 'Entrez le numéro de version de l\'artefact')
    }
    
    tools {
        maven 'MonMaven'
    }
    
    stages {
        stage('Affichage des Paramètres') {
            steps {
                echo "Lancement du build pour l'environnement : ${params.ENVIRONNEMENT}"
                echo "Version spécifiée : ${params.VERSION}"
            }
        }
        stage('Nettoyage & Préparation') {
            steps {
                echo 'Nettoyage de l\'espace de travail...'
                sh 'mvn clean'
            }
        }
        stage('Compilation') {
            steps {
                echo 'Compilation de l\'application...'
                sh "mvn compile"
            }
        }
        stage('Tests Unitaires') {
            steps {
                echo 'Exécution des tests unitaires...'
                sh 'mvn test'
            }
        }
        stage('SonarQube Analysis') {
            steps {
                echo "Analyse SonarQube pour la version ${params.VERSION}..."
                withSonarQubeEnv('SonarQube') {
                    sh 'mvn sonar:sonar'
                }
            }
        }
    }
}
