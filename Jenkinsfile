pipeline {
          agent { label 'jenkins-agent' }
                  tools {
                          jdk 'Java17'
                            maven 'Maven3'
                        }
          stages{
                  stage("cleanup Workspace"){
                        steps {
                                cleanWs()
                              }
                  }
                  stage("Checkout from SCM"){
                        steps {
                                git branch: 'main', credentialsId: 'github', url: 'https://github.com/Sushiel13/register-app'
                              }
                  }
                  stage("Build Application"){
                        steps {
                                sh "mvn clean package"
                              }
                  }
  

                 stage("Test Application"){
                       steps {
                               sh "mvn test"
                             }
                 }
                    stage("SonarQube Analysis"){
           steps {
	           script {
		        withSonarQubeEnv(credentialsId: 'jenkins-sonarqube-token') { 
                        sh "mvn sonar:Mh37f8800@washim"
          }
 }
           }                    
  }
