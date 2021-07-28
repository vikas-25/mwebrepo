

pipeline {
    agent any

stages {
        stage('CodeCheckout') {
            steps {
        git credentialsId: 'git_credentials', url: 'https://github.com/shashikanth-t/mwebrepo.git'        
		echo "Code Checkout done successfully."
                  }
                        }
        stage('CodeBuild') {
            steps {
               sh 'mvn clean install'
		echo "Code Build done successfully."
                  }
                        }
        stage('CodeDeploy') {
             steps {
		sshagent(['deploy_user']) {
  			
			sh'scp -o StrictHostKeyChecking=no  webapp/target/webapp.war  ec2-user@52.14.139.141:/opt/apache-tomcat-8.5.35/webapps'
            echo "Code deploy done successfully."

			}

		
                  }
                        }
      }
   


  }
