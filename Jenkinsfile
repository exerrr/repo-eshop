pipeline {
    agent any

    environment {
        DOTNET_HOME = "/c/Users/yourusername/.dotnet/tools"
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/exerrr/repo-eshop.git'
            }
        }

        stage('Verify Dotnet SDK') {
            steps {
                sh "${DOTNET_HOME}/dotnet --version"
            }
        }

        stage('Restore') {
            steps {
                sh "${DOTNET_HOME}/dotnet restore src/eShop.AppHost/eShop.AppHost.csproj"
            }
        }

        stage('Build') {
            steps {
                sh "${DOTNET_HOME}/dotnet build src/eShop.AppHost/eShop.AppHost.csproj --configuration Release"
            }
        }

        stage('Run') {
            steps {
                sh "${DOTNET_HOME}/dotnet run --project src/eShop.AppHost/eShop.AppHost.csproj"
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
