pipeline {
    agent any

    stages {
        stage('Clonar Repositorio') {
            steps {
                git credentialsId: 'juan', branch: 'main', url: 'https://github.com/Jcbarahon/Proyecto.git'
            }
        }

        stage('Instalar Dependencias') {
            steps {
                bat 'dotnet restore Proyecto.sln'
            }
        }

        stage('Compilar Proyecto') {
            steps {
                bat 'dotnet build Proyecto.sln --configuration Release'
            }
        }

        stage('Ejecutar Pruebas') {
            steps {
                bat 'dotnet test Proyecto.sln --logger trx --configuration Release'
            }
        }

        stage('Publicar Reportes de Pruebas') {
            steps {
                junit '**/TestResults/*.trx'
            }
        }
    }
}
