pipeline {
    agent any

    stages {
        stage('Restore the dependencies') {
            when { branch pattern: "(main|develop|feature/.*)", comparator: "REGEXP" }
            steps {
                sh 'dotnet restore'
            }
        }
        stage("Build the application"){
            when { branch pattern: "(main|develop|feature/.*)", comparator: "REGEXP" }
            steps{
                sh 'dotnet build --no-restore'
            }
        }
        stage("Run the tests"){
            when { branch pattern: "(main|develop|feature/.*)", comparator: "REGEXP" }
            steps{
                sh 'dotnet test --no-build --verbosity normal'
            }
        }
    }
}