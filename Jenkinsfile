node
{
 def mavenHome = tool name: "maven3.6.3"
 stage('checkoutCode')
 {
  git branch: 'development', credentialsId: '1ea4b49f-fb62-4284-a1bf-30da16305a43', url: 'https://github.com/madhu3410/maven-web-application.git'
 } 
 stage('Build')
 {
  sh "${mavenHome}/bin/mvn clean package"
 }
 stage('ExecuteSonarQubeReport')
 {
  sh "${mavenHome}/bin/mvn sonar:sonar"
 }
  stage('UploadArtifactintoNexus')
 {
  sh "${mavenHome}/bin/mvn deploy"
 }
 stage('DeployAppIntoTomcat')
 {
  sshagent(['b4375ee5-1af8-46f4-af10-8aab048e2d30'])
  {
   sh "scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@3.239.113.72:/opt/apache-tomcat-9.0.41/webapps/"
  }
 }
}
