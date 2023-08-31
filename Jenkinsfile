pipeline
{
    agent any
    stages
    {
        stage('continuousDownload')
        {
            steps
            {
                git 'https://github.com/Ajays566408/my_maven.git'
            }
        }
        stage('continuousBuild')
        {
            steps
            {
                sh 'mvn package'
            }
        }
        stage('continuousDeployment')
        {
            steps
            {
                deploy adapters: [tomcat9(credentialsId: 'a0094615-a03d-49f6-8ddb-dd938f787ea1', path: '', url: 'http://15.206.80.81:8080')], contextPath: 'testapp', war: '**/*.war'
            }
        }
        stage('continuousTesting')
        {
            steps
            {
                git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
                sh 'java -jar /home/ubuntu/.jenkins/workspace/Declarative_pipeline/testing.jar'
            }
        }
        stage('continuousDelivery')
        {
            steps
            {
                deploy adapters: [tomcat9(credentialsId: 'a0094615-a03d-49f6-8ddb-dd938f787ea1', path: '', url: 'http://3.110.33.178:8080')], contextPath: 'prodapp', war: '**/*.war'
            }
        }
    }
}
