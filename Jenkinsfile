pipeline {
    agent any

    stages {
        stage('Preparação do Ambiente') {
            steps {
                echo 'ja instalado'
            }
        }

        stage('Verificação do Ambiente') {
            steps {
                bat 'python --version'
                bat 'pip list'
                bat 'dir'
            }
        }

        stage('Execução do Teste Levenshtein') {
            steps {
                bat 'python3 levenshtein_teste.py'
            }
        }

        stage('Verificação do Arquivo de Perguntas') {
            steps {
                script {
                    if (fileExists('perguntas.txt')) {
                        echo 'Arquivo perguntas.txt encontrado!'
                    } else {
                        error('Arquivo perguntas.txt não encontrado. Interrompendo o pipeline.')
                    }
                }
            }
        }
        
        stage('Execução do Chatbot') {
            steps {
                bat 'python3 chat_bot.py'
            }
        }
    }
}
