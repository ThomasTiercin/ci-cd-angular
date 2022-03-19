pipeline {
    agent any
    triggers {
        githubPush()
    }
    stages {
        stage('Restore packages'){
           steps{
               bat 'dotnet restore my-new-app.sln'
            }
         }
        stage('Clean'){
           steps{
               bat 'dotnet clean my-new-app.sln --configuration Release'
            }
         }
        stage('Build'){
           steps{
               bat 'dotnet build my-new-app.sln --configuration Release --no-restore'
            }
         }
        stage('Test: Unit Test'){
           steps {
                bat 'dotnet test XUnitTestProject/XUnitTestProject.csproj --configuration Release --no-restore'
             }
          }
        stage('Publish'){
             steps{
               bat 'dotnet publish WebApplication/my-new-app.csproj --configuration Release --no-restore'
             }
        }
    }
}
