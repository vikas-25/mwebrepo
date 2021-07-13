pipeline {
    agent any

 stages {
        stage('Code Checkout ') {
            steps {
        git credentialsId: 'git_credentials', url: 'https://github.com/shashikanth-t/mwebrepo.git'        
		echo "code checkout done."
                  }
                                }
        stage('Code Build ') {
            steps {
            sh 'mvn clean install'    
		echo "code Build done."
                  }
                                }
        stage('Code Deploy ') {
            steps {
		sshagent(['deploy_user']) {
        sh "scp  -o StrictHostKeyChecking=no webapp/target/webapp.war  ec2-user@34.235.142.109:/opt/apache-tomcat-8.5.35/webapps"
                                          }
                  }
                                }
      }
}
