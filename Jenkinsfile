pipeline {
    agent any
    environment {
        PATH = "/opt/apache-maven-3.6.3/bin:$PATH"
    }
    stages {
        stage("clone code"){
            steps{
               //git credentialsId: 'git_credentials', url: 'https://github.com/ravdy/hello-world.git'
                git changelog: false, credentialsId: '0b85d8b1-aa4b-4753-b8aa-ce38971fd8fd', poll: false, url: 'https://github.com/shashikanth-t/mwebrepo.git'
            }
        }
        stage("build code"){
            steps{
              sh "mvn clean install"
            }
        }
        stage("deploy"){
            steps{
              sshagent(['deploy_user']) {
                 sh "scp -o StrictHostKeyChecking=no webapp/target/webapp.war ec2-user@3.142.149.74:/opt/apache-tomcat-8.5.35/webapps"
                
                }
            }
        }
    }
}
