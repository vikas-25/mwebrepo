pipeline {
    agent any
     environment {
       PATH = "/opt/maven/bin:$PATH"
                 }
    stages {
        stage('Code Checkout ') {
            steps {
                git 'https://github.com/vikas-25/mwebrepo.git'
                echo "code checkout is done"
            }
                             	}
        stage('Code Build ') {
            steps {
                sh 'mvn clean install'
                echo "code Build is done"
            }
                             	}
        stage('Code Deploy ') {
            steps {
                sshagent(credentials: ['deploy_user'], ignoreMissing: true) {
                sh "scp -o StrictHostKeyChecking=no webapp/target/webapp.war  ec2-user@18.191.206.148:/opt/apache-tomcat-8.5.35/webapps"
                  }
                echo "code Deploy is successfully done"
            }
                             	}                     	
                             	
            }
}
