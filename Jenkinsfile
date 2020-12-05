pipeline {
    agent any
    stages {
        stage('Compile') {
         steps {    
          sh 'mvn clean compile -e'
          }
         }
        stage('Test') {
         steps {
	        sh 'mvn clean test -e'
         }
        } 
      stage('Jar') {
        steps { 
         sh 'mvn clean package -e'
       }
      }
      stage('SonarQube analysis') {
        steps {
         installationName: 'Sonar Local') {
          sh '${scannerHome}/bin/sonar-scanner'
        }
       }
      }  
      stage('Run') {
        steps {
	       sh 'mvn spring-boot:run &'
       } 
      }
      stage('Wait up app') {
        steps {
	       sh 'sleep 10'
       } 
      }
      stage('Testing app') {
       steps {
         sh 'curl -X GET http://localhost:8081/rest/mscovid/test?msg=testing'
        }
       }
      stage('Result Chile') {
       steps {
        sh 'curl -X GET http://localhost:8081/rest/mscovid/estadoPais?pais=CHILE'
        }
       }
      stage('Result Mundial') {
       steps {
        sh 'curl -X GET http://localhost:8081/rest/mscovid/estadoMundial'
        }
       } 
      }
     }    
