pipeline {
    agent any

    triggers {
        cron('*/5 * * * *') // Ejecuta el job cada 5 minutos
    }

    stages {
        stage('Descargar código desde GitHub') {
            steps {
                git branch: 'main', url: 'https://github.com/SahernR/TestLive.git'
            }
        }
        stage('Desplegar aplicación en Equipo Local') {
            steps {
                script {
                    // Comando para compilar o ejecutar un archivo Java simple en Windows
                    bat '''
                        javac HolaMundo.java
                        java HolaMundo
                    '''
                }
            }
        }
    }

    post {
        success {
            echo 'Pipeline ejecutado correctamente. 🎉'
        }
        failure {
            echo 'Hubo un error en la ejecución del pipeline. ❌'
        }
    }
}
