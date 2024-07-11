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
                sh '"/c/Users/yourusername/.dotnet/tools/dotnet" --version' // Reemplaza yourusername con tu nombre de usuario real
            }
        }

        stage('Restore') {
            steps {
                sh '"/c/Users/yourusername/.dotnet/tools/dotnet" restore src/eShop.AppHost/eShop.AppHost.csproj'
            }
        }

        stage('Build') {
            steps {
                sh '"/c/Users/yourusername/.dotnet/tools/dotnet" build src/eShop.AppHost/eShop.AppHost.csproj --configuration Release'
            }
        }

        stage('Run') {
            steps {
                sh '"/c/Users/yourusername/.dotnet/tools/dotnet" run --project src/eShop.AppHost/eShop.AppHost.csproj'
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
