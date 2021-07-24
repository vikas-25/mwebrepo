pipeline {
    agent any
     PATH = "/opt/maven/bin:$PATH"
    
 stages {
        stage('Code Checkout ') {
            steps {   
                git credentialsId: 'git_credentials', url: 'https://github.com/shashikanth-t/mwebrepo.git'
                echo "Code Checkout done."
                   }
                             }
         stage('Code Build ') {
            steps {   
                 sh 'mvn clean install'
                echo "Code Build done."
                   }
                             }
        stage('Code Deploy ') {
            steps {  
            sshagent(['deploy_user']) {
           sh "scp -o StrictHostKeyChecking=no webapp/target/webapp.war ec2-user@34.230.55.102:/opt/apache-tomcat-8.5.35/webapps"               
                                    }    
                echo "code deploy done."
                   }
                             }                             
 }
}
