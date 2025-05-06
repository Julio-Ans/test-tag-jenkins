pipeline {
    agent any

    environment {
        TAG_NAME = ''
    }

    stages {
        stage('Preparar') {
            steps {
                script {
                    // Verifica se o commit atual está associado a uma tag
                    def tag = sh(script: 'git tag --points-at HEAD', returnStdout: true).trim()
                    if (tag) {
                        TAG_NAME = tag
                        echo "Commit associado à tag: ${TAG_NAME}"
                    } else {
                        echo "Nenhuma tag associada ao commit."
                    }
                }
            }
        }

        stage('Deploy') {
            when {
                expression { return TAG_NAME != '' }
            }
            steps {
                script {
                    echo "Iniciando deploy para a versão ${TAG_NAME}..."
                    // Adicione aqui os comandos específicos para o deploy
                }
            }
        }
    }
}

