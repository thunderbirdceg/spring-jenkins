pipeline{
 /* agent {
    label "docker-agent"
  }
  */
  agent any
  
  environment{
    registry= "trailfire/dockertest"
      registryCredentials='dockerhubgokul'
    
  }
  tools{
   maven 'Maven' 
    
  }
  

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
     dockerImage = docker.build registry + "spring" + "$BUILD_NUMBER" 
      }
    }
    
  }
  
  stage('Deploy Image') {
  steps{    script {
      docker.withRegistry( '', registryCredentials ) {
        dockerImage.push()
      }
    }
  }
  }

stage('Remove Unused docker image') {
  steps{
    sh "docker rmi $registry:$BUILD_NUMBER"
  }
}
  
  

}



}
