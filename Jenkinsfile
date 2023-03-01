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
                                version: "1.0-version",
                                repository: "raoua",
                                credentialsId: "nexus-connection", 
                                artifacts: [
                                    [artifactId: "yubikey coordonnée", 
                                     classifier: '',
                                     file: "http://10.50.250.70:8081/repository/raoua/yubikey%20coordonn%C3%A9e",
                                     type: "yubikey coordonnée.txt"]]);
          echo "hello , I'm deploying on nexus" 
      }
  
    } 
  
  }

}
