pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/Tomathiko/my-first-pipeline.git'
            }
        }
        stage('Instalar dependencias') {
            steps {
                sh 'npm install'
            }
        }
        stage('Ejecutar pruebas') {
            steps {
                sh 'npm test'
            }
        }
        stage('Desplegar') {
            steps {
                sh 'echo "Desplegando aplicación..."'
            }
        }
    }
}
