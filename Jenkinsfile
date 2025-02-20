pipeline{
  agent{ label 'Jenkins-Agent'}
  tools{
    jdk 'JDK 17'
    maven 'maven3'
  }
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
    stage("SonarQube Analysis"){
      steps{
        script{
          withSonarQubeEnv(credentialsId: 'jenkins-sonar-token'){
            sh "mvn sonar:sonar"
          }
        }
  }
  }
    stage("Quality Gate"){
      steps{
        script{
          waitForQualityGate abortPipeline: false, credentialsId: 'jenkins-sonar-token'
        }
      }
    }
  }
}

    
    
    
