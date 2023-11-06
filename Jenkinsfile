


node('built-in') 
{ 
     stage('ContinuousDownload') 
     {
        git 'https://github.com/krishnain/mavenproj.git' 
     }
     stage('ContinuousBuild')
     {
         sh 'mvn package'
     }
     stage('ContinuousDeployment')
     {
         deploy adapters: [tomcat9(credentialsId: '01c273a5-408a-47dc-ba02-a18cd347bf9e', path: '', url: 'http://172.31.29.134:9090')], contextPath: 'testapp', war: '**/*.war'
     }
     stage('ContinousTesting')
     {
         git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
     
         sh 'java -jar /var/lib/jenkins/workspace/ScriptedPipeline1/testing.jar'
     }
     stage('ContinuousDelivery')
     {
         
         deploy adapters: [tomcat9(credentialsId: '01c273a5-408a-47dc-ba02-a18cd347bf9e', path: '', url: 'http://172.31.23.5:9090')], contextPath: 'myprodapp', war: '**/*.war'
     }
     
     
}
