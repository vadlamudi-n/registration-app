pipeline{
  agent{ label 'Jenkins-Agent'}
  tools{
    jdk 'Java17'
    maven 'maven3'
  stages{
    stage("Clean Workspace"){
      steps{
        cleanWs()      
  }
  }
    stage("Check From SCM"){
      steps{
        git branch: 'main', credentialsId: 'github', url: 'https://github.com/vadlamudi-n/registration-app.git'
      }
    }
    stage("Build Application"){
      steps{
        sh "mvn clean package"
      }
    }
    stage("Test Application"){
      steps{
        sh "mvn test"
      }
    }
  }
  }
}
    
    
    
