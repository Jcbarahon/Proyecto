pipeline {
    agent any

    stages {
        stage('Clonar Repositorio') {
            steps {
                git branch: 'main', url: 'https://github.com/Usuario/MiProyecto.git'
            }
        }

        stage('Instalar Dependencias') {
            steps {
                bat 'dotnet restore MiProyecto.sln'
            }
        }

        stage('Compilar Proyecto') {
            steps {
                bat 'dotnet build MiProyecto.sln --configuration Release'
            }
        }

        stage('Ejecutar Pruebas') {
            steps {
                bat 'dotnet test MiProyecto.sln --logger trx --configuration Release'
            }
        }

        stage('Publicar Reportes de Pruebas') {
            steps {
                junit '**/TestResults/*.trx'
            }
        }
    }
}
