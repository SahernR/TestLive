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
                    // Define el directorio local para despliegue
                    def localDir = 'C:\\Users\\Sebastian\\Documents\\Ingenieria Informatica\\INTEGRACIÓN CONTINUA500-CED-4EVAS\\App'

                    // Crear el directorio si no existe y copiar archivos descargados
                    bat """
                    if not exist "${localDir}" mkdir "${localDir}"
                    xcopy /E /Y *.* "${localDir}"
                    """
                }
            }
        }
        stage('Compilar y ejecutar aplicación') {
            steps {
                script {
                    def localDir = 'C:\\Users\\Sebastian\\Documents\\Ingenieria Informatica\\INTEGRACIÓN CONTINUA500-CED-4EVAS\\App'

                    // Cambiar al directorio local y ejecutar los comandos de Java
                    bat """
                    cd "${localDir}"
                    javac HolaMundo.java
                    java HolaMundo
                    """
                }
            }
        }
    }

    post {
        success {
            echo 'Pipeline ejecutado correctamente en Windows. 🎉'
        }
        failure {
            echo 'Hubo un error en la ejecución del pipeline en Windows. ❌'
        }
    }
}
