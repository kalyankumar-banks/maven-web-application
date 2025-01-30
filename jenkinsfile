node{
    
def mavenHome = tool name: 'maven3.9.8'

properties([buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '5', daysToKeepStr: '', numToKeepStr: '5')), pipelineTriggers([pollSCM('* * * * *')])])

stage ('CheckOutCode'){
git branch: 'development', credentialsId: '3a454b1c-6ee5-4a9a-a427-e7c942b0cd25', url: 'https://github.com/kalyankumar-banks/maven-web-application.git'
}

stage('Build'){
sh "${mavenHome}/bin/mvn clean package"
}

/*
stage('ExecuteSonarQubeReport'){
sh "${mavenHome}/bin/mvn clean sonar:sonar"
}

stage ('UploadArtifactsIntoNexus'){
sh "${mavenHome}/bin/mvn clean deploy"
}

stage('DeployAppintoTomcatServer'){
sshagent(['992c78d9-b2b3-4dc2-ae61-ee07eee0c77f']) {
  sh "scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@172.31.34.37:/opt/apache-tomcat-9.0.98/webapps/"
}
}

*/

}
