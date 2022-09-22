node('built-in')
{
    stage('ContinuousDownload')
    {
        git 'https://github.com/intelliqittrainings/maven.git'
    }
    stage('ContinuosBuild')
    {
        sh 'mvn package'
    }
    stage('continuousDeployment')
    {
        deploy adapters: [tomcat9(credentialsId: '8f762d4a-66a8-4be7-a34d-97ebe4cd9186', path: '', url: 'http://172.31.0.193:8080')], contextPath: 'testapp', war: '**/*.war'
    }
    stage('continuosTesting')
    {
         git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
         sh 'java -jar /home/ubuntu/.jenkins/workspace/ScriptedPipeline1/testing.jar'
    }
    stage('continuosDelivery')
    {
        deploy adapters: [tomcat9(credentialsId: '7eb39faa-7376-419f-af32-abe4254149a3', path: '', url: 'http://172.31.10.216:8080')], contextPath: 'prodapp', war: '**/*.war'
    }
}
