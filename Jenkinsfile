pipeline {
    agent any
    environment {
        PATH = "/opt/maven/bin:$PATH"
    }
    stages {
        stage('Code Checkout ') {
           steps {
           git credentialsId: 'git_credentials', url: 'https://github.com/shashikanth-t/mwebrepo.git'
           echo "Code checkout done sucessfully."
                 }
                    }
            stage('Code build ') {
            steps {
            sh 'mvn clean install'
            echo 'Code build done sucessfully.'
            }
            }
	    stage('Code deploy ') {
            steps {
		sshagent(['deploy_user']) {
		sh "scp -o StrictHostKeyChecking=no webapp/target/webapp.war  ec2-user@18.234.180.228:/opt/apache-tomcat-8.5.35/webapps"
						}
				}
				
			}
}
}
