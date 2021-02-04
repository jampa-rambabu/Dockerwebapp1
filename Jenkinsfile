node{

def tomcatWeb = '/opt/tomcat/apache-tomcat-9.0.41/webapps/'
def tomcatBin = '/opt/tomcat/apache-tomcat-9.0.41/bin/'
def tomcatStatus = ''
stage('SCM Checkout')
  {
git 'https://github.com/jampa-rambabu/Dockerwebapp1.git'
}
stage('Compile-Package-Create-War-File')
  {
def mvnHome = tool name: 'Maven', type: 'maven'
sh "${mvnHome}/bin/mvn package"
}
stage('Deploy to War On Tomcat')
  {
    steps{
      sshagent(['deplyer']) {
    // some block
  sh "scp -o StrictHostKeyChecking=no pipelineTomcat/target/PersistentWebApp.war ec2-user@54.161.54.223:/opt/tomcat/apache-tomcat-9.0.41/webapps"  
}
}
  }
stage ('Start TomCat Server')
{
sleep(time:5,unit:"SECOUNDS")
sh "${tomcatBin}"//startup.sh
sleep(time:100,unit:"SECOUNDS")
}
}
