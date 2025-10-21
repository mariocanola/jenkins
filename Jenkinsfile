pipeline {
    agent any

    stages {
        stage('Instalar dependencias') {
            steps {
                sh '''
                    python3 -m venv venv
                    . venv/bin/activate
                    pip install -r requirements.txt || echo "No hay archivo requirements.txt"
                '''
            }
        }

        stage('Ejecutar pruebas') {
            steps {
                sh '''
                    . venv/bin/activate
                    python3 test_main.py
                '''
            }
        }
    }

    post {
        success {
            echo 'Pipeline ejecutado correctamente.'
        }
        failure {
            echo 'Ocurrió un error en la ejecución del pipeline.'
        }
    }
}