
pipeline {
    agent any
	 environment {
        PATH = "/opt/maven/bin:$PATH"
        }
	stages {
        stage('CodeCheckout') {
            steps { 
            git credentialsId: 'git_credentials', url: 'https://github.com/shashikanth-t/mwebrepo.git'    
			echo "Code Checkout done."
			}
			          }
        stage('CodeBuild') {
            steps { 
            sh 'mvn clean install'    
			echo "Code Build done."
			}
			                     }	
        stage('CodeDeploy ') {
            steps { 
            sshagent(['deploy_user']) {
            sh "scp  -o StrictHostKeyChecking=no webapp/target/webapp.war   ec2-user@13.235.79.139:/opt/apache-tomcat-8.5.35/webapps"
                }    
			echo "CodeDeploy done."
			}
			                     }
			}					 


}
