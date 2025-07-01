ipipeline {
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
        stage("build-image") {
             steps {
		    sh 'sudo docker build -t tomcat-repo:$BUILD_TAG .'
                    sh 'sudo docker tag tomcat-repo:$BUILD_TAG bhimsinghdig/docklogin'
                    }
                 }
	} 
}
