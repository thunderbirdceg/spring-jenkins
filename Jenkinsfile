pipeline{
  environment{
    registry= "trailfire/dockertest"
      registryCredentials='dockerhubgokul'
    
  }
  tools{
   maven 'Maven' 
    
  }
  
agent any
stages{
stage('Build'){
  steps{
echo'Hi'
    sh 'mvn clean install'
    echo "${env.BUILD_ID}"
  }
}
  stage('Docker'){
    steps{
      script
      {
      docker.build registry + "spring" + "$BUILD_NUMBER" 
      }
    }
    
  }



}



}
