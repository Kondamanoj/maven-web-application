node{
    
echo "Job name is: ${env.JOB_NAME}"
echo "Build Number is: ${env.BUILD_NUMBER}"
echo "Jenkins Home is: ${env.JENKINS_HOME}"
echo "Build Number is: ${env.BUILD_NUMBER}"
    
properties([buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '5', daysToKeepStr: '', numToKeepStr: '5')), [$class: 'JobLocalConfiguration', changeReasonComment: ''], pipelineTriggers([pollSCM('* * * * *')])])

    def mavenHome = tool name: 'mavan3.9.8'

stage('CheckOutCode'){
git branch: 'development', credentialsId: '7567ab5d-6760-4632-8580-7b85864b5901', url: 'https://github.com/Kondamanoj/maven-web-application.git'
}

stage('Build'){
sh "${mavenHome}/bin/mvn clean package"
}
/*
stage('ExecuteSonarQubeReport'){
sh "${mavenHome}/bin/mvn clean sonar:sonar"
}

stage('UploadArtifactIntoNexus'){
sh "${mavenHome}/bin/mvn clean deploy"
}

stage('DeployAppIntoTomcat'){
sshagent(['dd598275-2901-4265-ab2c-b5ff943cb025']) {
 sh "scp -o StrictHostkeyChecking=no target/maven-web-application.war ec2-user@172.31.37.22:/opt/apache-tomcat-9.0.90/webapps/"
}
}
*/
}
