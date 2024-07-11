pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        /* stage('Verify Dotnet SDK') {
            steps {
                script {
                    def dotnet = dotnetVersion()
                    echo "Dotnet SDK version: ${dotnet}"
                }
            }
        } */

        stage('Restore') {
            steps {
                script {
                    sh 'dotnet restore src/eShop.AppHost/eShop.AppHost.csproj'
                }
            }
        }

        stage('Build') {
            steps {
                script {
                    sh 'dotnet build src/eShop.AppHost/eShop.AppHost.csproj --configuration Release'
                }
            }
        }

        stage('Run') {
            steps {
                script {
                    sh 'dotnet run --project src/eShop.AppHost/eShop.AppHost.csproj'
                }
            }
        }
    }

    post {
        always {
            archiveArtifacts artifacts: '**/bin/Release/*.dll', allowEmptyArchive: true
        }
    }
}
