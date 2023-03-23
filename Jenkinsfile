pipeline {
    agent any
    tools{
        maven "maven3.8.6"
    }
    stages{
        stage("git checkout"){
            steps{
                git 'https://github.com/github2org/mani-jw-app-docker.git'
            }
        }
        stage("Maven Build"){
            steps{
                sh "mvn clean package"
            }
        }
      stage("Deploy to Tomcat"){
           steps{
               sshagent(['Tomcat_creds']) {
                 sh "scp -o StrictHostKeyChecking=no target/java-web-app-1.0.war  ec2-user@13.235.23.85:/opt/apache-tomcat-9.0.73/webapps/"

}
           }
      }
    }
}
