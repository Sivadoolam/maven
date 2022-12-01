node('built-in') 
{
    stage('ContinuousDownload')
    {
       git 'https://github.com/intelliqittrainings/maven.git'
    }
    stage('ContinuousBuild')
    {
       sh 'mvn package'
    }
    stage('ContinuousDeployment')
    {    
         deploy adapters: [tomcat9(credentialsId: '855bac34-c216-4677-87a5-dbd50836f45e', path: '', url: 'http://172.31.32.214:8080')], contextPath: 'testapp', war: '**/*.war'        
    }           
    stage('ContinuousTesting')
    { 
       git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
       sh 'java -jar /var/lib/jenkins/workspace/scriptedPipeline/testing.jar'
   
   
    }
    stage('ContinuousDelivery') 
    {
       deploy adapters: [tomcat9(credentialsId: '855bac34-c216-4677-87a5-dbd50836f45e', path: '', url: 'http://172.31.42.198:8080')], contextPath: 'prodapp', war: '**/*.war'
    }
      
      
      

      
    
}    
