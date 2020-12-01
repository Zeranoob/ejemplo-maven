pipeline {
    agent any
    stages {
        stage('Compile') {
         steps {    
          dir("/home/anonymous/Música/TallerS4/ejemplo-maven") {
	       sh 'mvn clean compile -e'
           }
          }
         }
        stage('Test') {
         steps {
          dir("/home/anonymous/Música/TallerS4/ejemplo-maven") {
	       sh 'mvn clean test -e'
          }
         }
        } 
      stage('Jar') {
        steps { 
         dir("/home/anonymous/Música/TallerS4/ejemplo-maven") {
	      sh 'mvn clean package -e'
        }
       }
      } 
      stage('Run') {
        steps {
         dir("/home/anonymous/Música/TallerS4/ejemplo-maven") {
	      sh 'mvn spring-boot:run &'
        }
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
      stage('Result Sonar') {
       steps {
        sh 'mvn sonar:sonar \
             -Dsonar.projectKey=Taller_S6_M3 \
              -Dsonar.host.url=http://localhost:9000/sonarqube \
               -Dsonar.login=0393dedba260787229fbf470f821ac0aeccfe38b'
         }
        }  
       }
      }  