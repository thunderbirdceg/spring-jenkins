pipeline{
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




}



}
