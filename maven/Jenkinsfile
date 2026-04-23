pipeline
{
    agent any
    stages
    {
stage('ContinuousDownload')
        {
            steps
            {
              git 'https://github.com/IntelliqDevops/maven.git'  
            }
        }

stage('ContinuousBuild')
        {
            steps
            {
              sh 'mvn package' 
            }
        }
            
stage('ContinuousDeployment')
        {
            steps
            {
              deploy adapters: [tomcat9(alternativeDeploymentContext: '', credentialsId: '545cd0ee-a4ac-4ebd-870d-80dc523ef754', path: '', url: 'http://172.31.20.42:8080')], contextPath: 'test1', war: '**/*.war'
            }
        }
            
            
stage('ContinuousTesting')
        {
            steps
            {
              git 'https://github.com/IntelliqDevops/FunctionalTesting.git'
              sh 'java -jar /var/lib/jenkins/workspace/DeclarativePipeline1/testing.jar'
            }
        }
            
            
stage('ContinuousDelivery')
        {
            steps
            {
              deploy adapters: [tomcat9(alternativeDeploymentContext: '', credentialsId: '545cd0ee-a4ac-4ebd-870d-80dc523ef754', path: '', url: 'http://172.31.30.29:8080')], contextPath: 'prod1', war: '**/*.war'
            }
            
        }           
            
        }
        }
