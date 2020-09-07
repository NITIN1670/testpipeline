pipeline 
{
    agent any
     environment 
    {

       sonarscannerdotnet = tool name : 'sonar_scanner_dotnet', type='hudson.plugins.sonar.MsBuildSQRunnerInstallation'
    }

    stages 
    {
        stage('Start sonarqube analysis')
        {
             steps 
            {
                 withSonarQubeEnv('Test_Sonar')
                 {
                    bat 'dotnet ${sonarscannerdotnet}/SonarScanner.MSBuild.dll begin /k:WebApplication4 /n:WebApplication4 /v:1'
                 }
             
            }
        }
        stage('End sonarqube analysis') 
        {
            steps 
            {
                withSonarQubeEnv('Test_Sonar')
                sh  'dotnet ${sonarscannerdotnet}/SonarScanner.MSBuild.dll end'
            }
        }
    }
}
