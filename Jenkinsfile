pipeline{
    agent any
  stages{
    
    stage("build"){
      steps{
          sh ` sudo apt install gcc & gcc -o fonction fonction.c & ./fonction `
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
                                    [artifactId: "fonction", 
                                     classifier: '',
                                     file: "fonction.c",
                                     type: ".c"]]);
          echo "hello , I'm deploying on nexus" 
      }
  
    } 
  
  }

}
