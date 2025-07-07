pipeline {
    agent any

    stages{
        stage ("saludo a usuario") {
            steps {
                sh 'echo "comenzado mi pipeline"'
            }
        }
        stage ("salida de los saludos a usuario") {
            steps {
                sh 'echo "saliendo de este grupo de escenarios"'
            }
        }
        stage ("proceso de build y test") {
            agent {
                docker {
                    image 'node:22'
                    reuseNode true
                }
            }
            stages {
                stage("instalacion de dependencias"){
                    steps {
                        sh 'npm ci'
                    }
                }
                stage("ejecucion de pruebas"){
                    steps {
                        sh 'npm run test:cov'
                    }
                }
                stage("construccion de la aplicacion"){
                    steps {
                        sh 'npm run build'
                    }
                }
            }
        }
    }
}