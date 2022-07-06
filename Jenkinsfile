node {
	
    def application = "devopsexample"
    
    //Its mandatory to change the Docker Hub Account ID after this Repo is forked by an other person
    def dockerhubaccountid = "1081081243"
	
    // reference to maven
    // ** NOTE: This 'maven-3.6.3' Maven tool must be configured in the Jenkins Global Configuration.   
    def mvnHome = tool 'local_maven'

    // holds reference to docker image
    def dockerImage
 
    def dockerImageTag = "${dockerhubaccountid}/${application}:${env.BUILD_NUMBER}"
  
    stage('Build Project') {
      // build project via maven
      sh "'${mvnHome}/bin/mvn' clean install"
    }
		
    stage('Build Docker Image with new code') {
      // build docker image
      dockerImage = docker.build("${dockerhubaccountid}/${application}:${env.BUILD_NUMBER}")
    }
}
