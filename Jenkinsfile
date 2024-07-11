pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/exerrr/repo-eshop.git'
            }
        }

        stage('Verify Dotnet SDK') {
            steps {
                sh 'dotnet --version' // Verifica que el SDK de .NET esté disponible
            }
        }

        stage('Restore') {
            steps {
                sh 'dotnet restore src/eShop.AppHost/eShop.AppHost.csproj'
            }
        }

        stage('Build') {
            steps {
                sh 'dotnet build src/eShop.AppHost/eShop.AppHost.csproj --configuration Release'
            }
        }

        stage('Run') {
            steps {
                sh 'dotnet run --project src/eShop.AppHost/eShop.AppHost.csproj'
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
