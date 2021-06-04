pipeline {
    agent any
    environment {
        PATH = "/opt/maven/bin:$PATH"
    }
    stages {
        stage('Code Checkout ') {
            steps {
                git credentialsId: '2f663736-522f-4420-9da2-dcaf697631e9', url: 'https://github.com/shashikanth-t/mwebrepo.git'
                echo 'Code Checkout done sucessfully.'
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
		sh "scp -o StrictHostKeyChecking=no webapp/target/webapp.war  ec2-user@54.198.222.245:/opt/apache-tomcat-8.5.35/webapps"
						}
				}
				
			}
        }
    }
