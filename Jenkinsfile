pipeline {
    agent any

    stages {
        stage("pull-scm") {
             steps {
                   git branch: 'main', url: 'https://github.com/bhimsinghdig/logindocker.git'
                   }
               }
	stage("build") {  
             steps {
	            sh 'sudo mvn clean package'
		    } 				   
	         }
	stage("build-image") {
             steps {
	            sh 'sudo docker build -t tomcat-repo:$BUILD_TAG .'
                    sh 'sudo docker tag tomcat-repo:$BUILD_TAG bhimsinghdig/docklogin:$BUILD_TAG'
		    } 				
                 }
        stage("dockerlogin") {
             steps {
                    withCredentials([string(credentialsId: 'login_pass', variable: 'log_var')]) {
                    sh 'sudo docker login -u bhimsinghdig -p ${login_var}'
                    sh 'sudo docker push bhimsinghdig/docklogin:$BUILD_TAG'
                    }
                  }
             }
        }
}
