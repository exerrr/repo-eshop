pipeline {
    agent any

    environment {
        PATH = "C:\\Users\\yourusername\\.dotnet\\tools;" + env.PATH
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/exerrr/repo-eshop.git'
            }
        }

        stage('Verify Dotnet SDK') {
            steps {
                bat 'dotnet --version' // Verifica que el SDK de .NET esté disponible
            }
        }

        stage('Restore') {
            steps {
                bat 'dotnet restore src/eShop.AppHost/eShop.AppHost.csproj'
            }
        }

        stage('Build') {
            steps {
                bat 'dotnet build src/eShop.AppHost/eShop.AppHost.csproj --configuration Release'
            }
        }

        stage('Run') {
            steps {
                bat 'dotnet run --project src/eShop.AppHost/eShop.AppHost.csproj'
            }
        }
    }

    post {
        always {
            archiveArtifacts artifacts: '**/bin/**/*', allowEmptyArchive: true
        }
        success {
            echo 'Pipeline succeeded!'
        }
        failure {
            echo 'Pipeline failed!'
        }
    }
}
