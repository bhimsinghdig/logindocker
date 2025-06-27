pipeline {
    agent any

    stages {
        stage("pull-scm") {
            steps {
                   git branch: 'main', url: 'https://github.com/bhimsinghdig/java-test-project.git'
                   }
               }
	stage("build") {  
             steps {
	            sh 'sudo mvn clean package'
		    } 				   
		  }				
        } 
}
