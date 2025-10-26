pipeline{
  agent any
  environment{
    PATH="$PATH:/opt/Maven-3.0.11/bin"
  }
  stages{
   stage('GetCode'){
    steps{
	 git'https://github.com/Mo-Adnan-Mo-Ayyub/Jenkins-webapp-deployment.git'
	 }
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
     sh"mvn soanr:sonar"
  }
  }
  }
}