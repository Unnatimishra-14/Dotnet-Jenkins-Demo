pipeline {
    agent any
    environment {
        dotnet = 'C:\\Program Files\\dotnet\\dotnet.exe'
    }
    stages {
        stage('Checkout Stage') {
            steps {
                git credentialsId: 'bf88affd-2ec0-4b45-b288-992012798d2a', url: 'https://github.com/Unnatimishra-14/Dotnet-Jenkins-Demo.git', branch: 'master'
            }
        }
        stage('Build Stage') {
            steps {
                bat 'C:\\ProgramData\\Jenkins\\.jenkins\\workspace\\Dotnet_jenkins_demo\\DotnetApp.sln --configuration Release'
            }
        }
        stage('Test Stage') {
            steps {
                bat 'dotnet test %WORKSPACE%\\DotnetApp\\DotnetApp.csproj'
            }
        }
        stage("Release Stage") {
            steps {
                bat 'dotnet build %WORKSPACE%\\DotnetApp.sln /p:PublishProfile=" %WORKSPACE%\\DotnetApp\\Properties\\PublishProfiles\\FolderProfile.pubxml" /p:Platform="Any CPU" /p:DeployOnBuild=true /m'
            }
        }
        stage('Deploy Stage') {
            steps {
                //Deploy application on IIS
                bat 'net stop "w3svc"'
                bat '"C:\\Program Files (x86)\\IIS\\Microsoft Web Deploy V3\\msdeploy.exe" -verb:sync -source:package="%WORKSPACE%\\DotnetApp\\bin\\Debug\\net8.0\\DotnetApp.zip" -dest:auto -setParam:"IIS Web Application Name"="Demo.Web" -skip:objectName=filePath,absolutePath=".\\\\PackagDemoeTmp\\\\Web.config$" -enableRule:DoNotDelete -allowUntrusted=true'
                bat 'net start "w3svc"'
            }
        }
    }
}
