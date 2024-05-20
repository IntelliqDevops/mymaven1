pipeline
{
    agent any
    stages
    {
        stage('ContDownload')
        {
            steps
            {
                git 'https://github.com/intelliqittrainings/maven.git'
            }
        }
        stage('ContBuild')
        {
            steps
            {
                sh 'mvn package'
            }
        }
        stage('ContDeployment')
        {
            steps
            {
               deploy adapters: [tomcat9(credentialsId: 'bd6501d1-4dff-4425-9d8c-ade9901715f1', path: '', url: 'http://172.31.29.188:9090')], contextPath: 'test1', war: '**/*.war'
            }
        }
        stage('ContTesting')
        {
            steps
            {
                git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
                sh 'java -jar /var/lib/jenkins/workspace/DeclarativePipeline1/testing.jar'
            }
        }
        stage('ContDelivery')
        {
            steps
            {
                deploy adapters: [tomcat9(credentialsId: 'bd6501d1-4dff-4425-9d8c-ade9901715f1', path: '', url: 'http://172.31.17.234:9090')], contextPath: 'prod1', war: '**/*.war'
            }
        }
        
        
        
        
        
        
        
        
        
    }
}
