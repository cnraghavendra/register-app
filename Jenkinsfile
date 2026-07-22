pipeline {
    agent { label 'Jenkins-Agent' }
    tools {
        jdk 'Java 21'
        maven 'Maven3'
    }
    stages {
        stage("Cleanup Workspace"){
                  steps {
                  CleanWs()
                  }
        } 

        stage("Checkout from SCM"){ 
            steps {
            git branch: 'main', credentialsId: 'github', url: 'https://github.com/cnraghavendra/register-app'
            }
        }  
      
        stage("Build Application"){
            steps {
                sh 'mvn clean package'
            }
        } 

        stage("Test Application"){
            steps {
                sh 'mvn test'
            }
        }  
    }
}
