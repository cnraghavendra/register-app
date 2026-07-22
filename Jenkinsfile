pipeline {
    agent { label 'Jenkins-Agent' }
    tools {
        jdk 'Java21'
        maven 'Maven3'
    }
    stages {
        stage("Cleanup Workspace"){
                  steps {
                  cleanWs()
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
        stage("Sonarqube Analysis"){
            steps {
                scripts { 
                    withSonarQubeEnv(credentialsId: 'jenkins-sonarqube-token'){
                        sh "mvn sonar:sonar"
                       }
                }
            }
        }                        
                
    }
}
