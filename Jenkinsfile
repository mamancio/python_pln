pipeline {
    agent any

    environment { PATH = "C:\\Windows\\System32;C:\\Users\\matheus.mancio\\AppData\\Local\\Programs\\Python\\Python312;C:\\Users\\matheus.mancio\\AppData\\Local\\Programs\\Python\\Python312\\Scripts;${env.PATH}"
    
    }
    parameters {
        string(name: 'DIRETORIO', description: 'Faça uma pergunta')
    }

    stages {
        stage('Preparação do Ambiente') {
            steps {
                echo 'ja instalado'
            }
        }

        stage('Execução do Teste Levenshtein') {
            steps {
                bat 'python levenshtein_teste.py'
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
                echo 'Interaja com o chatbot no console.'
                bat 'python chat_bot.py'
            }
        }
    }
}
