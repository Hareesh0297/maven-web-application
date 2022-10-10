node {

def mavenHome = tool name: "maven3.8.6"
stage('chcekoutCode'){

git branch: 'uat', credentialsId: '9c8ba476-2469-4e26-b28d-2334cc6bb31e', url: 'https://github.com/Hareesh0297/maven-web-application.git'

}
stage('Build'){

sh "${mavenHome}/bin/mvn clean package"

}
stage('SonarReport'){
    sh "${mavenHome}/bin/mvn sonar:sonar"
}
stage('DeploytoTomcat'){
    
sshagent(['9b1cf1c5-829a-449a-9e43-2aa8f0702e59']) {
    
sh "scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@3.109.182.185://opt/apache-tomcat-8.5.82/webapps"
}
}
}
