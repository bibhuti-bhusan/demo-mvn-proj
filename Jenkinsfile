pipeline {
      agent any
	tools{
	    maven 'maven'
	    jdk 'jdk1.8'
	}
	stages {

	   stage ('compile stage') {
	    steps {
		sh 'mvn clean compile'
		}   
	   }
	
	   stage ('Testing stage') {
            steps {
                sh 'mvn test'
                }
           }

	   stage ('package stage') {
            steps {
		sh 'mvn package'
                }
           }
	   
	   stage ('install stage') {
            steps {
                sh 'mvn install'
                }
           }

	   stage ('deployment stage') {
            steps {
                sh 'mvn deploy'
                }
           }
	   stage ('deployment-to-tomcat') {
            steps {
               sshagent(['tomcat-admin']) {
                sh 'scp -o StrictHostKeyChecking=no  target/*.war root@192.168.1.250:/opt/apache-tomcat/webapps/'
              }
            }
           }

	}
}
