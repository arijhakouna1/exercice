pipeline{
    agent any
  stages{
    
    stage("build"){
      steps{
        
          echo "hello , I'm building" 
          }
      }
      
    stage("test"){
      steps{
          echo "hello , I'm testing" 
      }
  
    } 
  stage("teste de qualité"){
      steps{
           withSonarQubeEnv('sonarqube') {
         
                 echo "hello , I'm testing quality"  
                }
      }
  
    } 
     stage("deploy-nexus"){
      steps{
          nexusArtifactUploader(
                                nexusVersion: "nexus 3",
                                protocol: "http" ,
                                nexusUrl: "10.50.250.70:8081" ,
                                groupId: "my",
                                version: "1",
                                repository: "raoua",
                                credentialsId: "nexus-connection", 
                                artifacts: [
                                    [artifactId: "fonction", 
                                     classifier: '',
                                     type: "c",
                                     file: "fonction-1.c"]]);
          echo "hello , I'm deploying on nexus" 
      }
  
    } 
  
  }

}
