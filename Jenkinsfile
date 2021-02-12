
node
{
 def mavenHome = tool name: "maven3.6.2"
 stage('checkoutCode')
 {
  git branch: 'development', credentialsId: '61a46d8a-5e67-49f5-ac72-4fdc9e4276af', url: 'https://github.com/madhu3410/maven-web-application.git'
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
  sshagent(['e2eff438-bd1d-4517-a893-3ceb497eb60e'])
  {
   sh "scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@18.207.135.7:/opt/apache-tomcat-9.0.41/webapps/"
  }
 }
}
