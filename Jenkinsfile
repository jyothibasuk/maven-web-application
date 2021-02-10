
node
{
  def mavenHome = tool name: "maven3.6.2"

 stage('ChecloutCode')
 {
  git branch: 'development', credentialsId: '4145d8d3-92a5-47df-8eef-7ef72011777a', url: 'https://github.com/madhu3410/maven-web-application.git'
 }

 stage('Build')
 {
  sh "${mavenHome}/bin/mvn clean package"
 }
 /*
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
  sshagent(['7e3a4ba9-d6c3-4ac0-ac47-cc140e454906'])
  {
   sh "scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@3.239.90.1:/opt/apache-tomcat-9.0.41/webapps/"
  }
 }
 
 stage('SendEmailNotification')
 {
     mail bcc: '', body: '''Build Over..

Regards,
Madhu.''', cc: 'gmb3410@gmail.com', from: '', replyTo: '', subject: 'Build Over', to: 'gayathri3410@gmail.com'
 }
 */
}
