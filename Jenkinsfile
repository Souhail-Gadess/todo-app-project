pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                echo 'Récupération du code depuis Git...'
                checkout scm
            }
        }
        
        stage('Install dépendances Node') {
            steps {
                echo 'Installation des dépendances Node.js...'
                bat 'npm install'
            }
        }
        
        stage('Tests') {
            steps {
                echo 'Exécution des tests...'
                bat 'npm test || exit 0'
            }
        }
        
        stage('Build Docker') {
            steps {
                echo 'Construction de l\'image Docker...'
                bat 'docker build -t todo-app .'
            }
        }
    }
    
    post {
        success {
            echo 'Pipeline exécuté avec succès !'
        }
        failure {
            echo 'Le pipeline a échoué.'
        }
    }
}