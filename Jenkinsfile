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
                deploy adapters: [tomcat9(credentialsId: 'd3795439-8ed0-41ff-9cc7-0788daec59c1', path: '', url: 'http://172.31.29.188:9090')], contextPath: 'newtestapp', war: '**/*.war'
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
                deploy adapters: [tomcat9(credentialsId: 'd3795439-8ed0-41ff-9cc7-0788daec59c1', path: '', url: 'http://172.31.17.234:9090')], contextPath: 'newprodapp', war: '**/*.war'
            }
        }
        
        
        
        
        
        
        
        
        
    }
}
