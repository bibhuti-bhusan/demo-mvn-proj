pipeline {
	agent any
	
	stages {
	   stage ('compile stage') {
	    steps {
	      withMaven(maven: 'mvn') {
		sh 'mvn clean compile'
	      }
	    }   
	   }
	
	   stage ('Testing stage') {
            steps {
              withMaven(maven: 'mvn') {
                sh 'mvn test'
              }
            }
           }

	   stage ('package stage') {
            steps {
              withMaven(maven: 'mvn') {
                sh 'mvn package'
              }
            }
           }
	   
	   stage ('install stage') {
            steps {
              withMaven(maven: 'mvn') {
                sh 'mvn install'
              }
            }
           }

	   stage ('deployment stage') {
            steps {
              withMaven(maven: 'mvn') {
                sh 'mvn deploy'
              }
            }
           }

	}
}
