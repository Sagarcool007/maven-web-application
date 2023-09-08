node {
   echo "jenkins home dir is: ${env.JENKINS_HOME}"
echo "job name is: ${env.JOB_NAME}"
echo "build number is: ${env.BUILD_NUMBER}"
    def mavenHome=tool name: 'maven3.9.3'
    properties([buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '5', daysToKeepStr: '', numToKeepStr: '5')), [$class: 'RebuildSettings', autoRebuild: false, rebuildDisabled: false], [$class: 'JobLocalConfiguration', changeReasonComment: ''], pipelineTriggers([pollSCM('* * * * *')])])
stage('CheckOutCode'){
git branch: 'development', credentialsId: 'f3b5abcd-971e-4ed0-9465-7e7c7dbe424c', url: 
'https://github.com/Sagarcool007/maven-web-application.git'
}
stage ('build'){
sh "${mavenHome}/bin/mvn clean package"
    
}

stage ('ExecuteSonarQubeReport') {
sh: "${mavenHome}/bin/mvn  clean sonar:sonar"
}
stage ('UploadArtifactsIntoNexus') {
sh: "${mavenHome}/bin/mvn  clean deploy"
} 

} 
