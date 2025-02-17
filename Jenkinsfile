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
pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                // Instalar dependencias y construir el proyecto
                sh 'npm install'
                sh 'npm run build'
            }
        }

        stage('Deploy') {
            steps {
                // Autenticación en Vercel con el token
                withCredentials([string(credentialsId: 'vercel-token', variable: 'VERCEL_TOKEN')]) {
                    // Desplegar en Vercel usando el token configurado
                    sh 'vercel --token UahUuGCdx8ttQQTQUaruxfCs --prod --yes'
                }
            }
        }
    }

    post {
        success {
            echo 'Despliegue completado con éxito en Vercel!'
        }
        failure {
            echo 'Error en el despliegue, revisa los logs!'
        }
    }
}
