pipeline {
      agent any	
      stages {

	   stage ('compile stage') {
	    steps {
	      maven(maven: 'maven') {
		sh 'mvn clean compile'
	      }
	    }   
	   }
	
	   stage ('Testing stage') {
            steps {
              maven(maven: 'maven') {
                sh 'mvn test'
              }
            }
           }

	   stage ('package stage') {
            steps {
              maven(maven: 'maven') {
                sh 'mvn package'
              }
            }
           }
	   
	   stage ('install stage') {
            steps {
              maven(maven: 'maven') {
                sh 'mvn install'
              }
            }
           }

	   stage ('deployment stage') {
            steps {
              maven(maven: 'maven') {
                sh 'mvn deploy'
              }
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
