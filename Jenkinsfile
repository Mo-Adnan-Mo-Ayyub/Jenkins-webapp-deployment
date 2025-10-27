pipeline {
  agent any
  environment{
    PATH="$PATH:/opt/Maven-3.0.11/bin"
  }
  stages {
   stage('GetCode'){
    steps{
   git 'https://github.com/Mo-Adnan-Mo-Ayyub/Jenkins-webapp-deployment.git'
   }
  }
  stage('Build'){
   steps{
	sh 'mvn clean package'
	}
  }
  stage('SonarQube analysis'){
   steps{
    withSonarQubeEnv('sonar-server-10.6'){
     sh "mvn sonar:sonar"
  }
  }
  }
  stage('Code Deploy'){
    steps{
      sshagent(['Tomcat-server']) {
        sh 'scp -o StrictHostKeyChecking=no target/jenkins-webapp-deployment.war ubuntu@54.237.99.232:/home/ubuntu/apache-tomcat-9.0.111/webapps'

    }
  }
  }
}
}