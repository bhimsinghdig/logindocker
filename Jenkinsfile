pipeline {
    agent any

    stages {
        stage("pull-scm") {
            steps {
                git branch: 'main', url: 'https://github.com/bhimsinghdig/java-test-project.giti'
            }
        }

        stage("build") {
            steps {
                sh 'mvn clean package'
            }
        }

        stage("test") {
            steps {
                sh 'java -jar target/*.jar > text.txt'
            }
        }
    }
}
