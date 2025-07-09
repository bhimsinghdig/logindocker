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
                    withCredentials([string(credentialsId: 'loginpass', variable: 'loginvar')]) {
                    sh 'sudo docker login -u bhimsinghdig -p ${loginvar}'
                    sh 'sudo docker push bhimsinghdig/docklogin:$BUILD_TAG'
		    }
	        }
	   }
        stage("QAT") {
             steps {
                   sh 'sudo docker rm -f $(sudo docker ps -a -q)'
                   sh 'sudo docker run -dt --name web1 -p 8087:8080 bhimsinghdig/pipeline-java:$BUILD_TAG'

                   }
                }
       }
}
