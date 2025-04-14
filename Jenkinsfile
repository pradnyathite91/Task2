pipeline {
    agent {
        label{
            label "built-in"
            customWorkspace "/mnt/test"
        }
    }
	
	tools {
        maven 'Maven'  
    }

    stages {
        stage('Clone Repo') {
            steps {
                git 'https://github.com/Shantanumajan6/project.git'
            }
        }

        stage('mvn') {
            steps {
                   sh "mvn clean install"
            }
        }
         stage('Remove existing container') {
             steps {
               script {
                sh '''
                docker ps -q -f name=c1 && docker kill c1 || true
                docker ps -a -q -f name=c1 && docker rm c1 || true
                   '''
                }
            }
        }
		
        stage('Run Docker Container') {
            steps {
                script {
                    sh 'docker run -d -p 8081:8080 --name c1 tomcat'
                }
            }
        }
        
        
        stage('copy war') {
            steps {
                  sh "docker cp /mnt/test/target/LoginWebApp.war c1:/usr/local/tomcat/webapps/"
            }
        }
    }
}
