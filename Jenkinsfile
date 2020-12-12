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
      stage('sonar') {
          steps {
          withSonarQubeEnv(installationName: 'Sonar') {     
        }
       }
      }  
      stage('uploadNexus') {
          steps {
          nexusPublisher nexusInstanceId: 'nexus', nexusRepositoryId: 'test-nexus', packages: [[$class: 'MavenPackage', mavenAssetList: [[classifier: '', extension: 'jar', filePath: '/home/anonymous/Música/TallerS4/ejemplo-maven/build/DevOpsUsach2020-0.0.1.jar']], mavenCoordinate: [artifactId: 'DevOpsUsach2020', groupId: 'com.devopsusach2020', packaging: 'jar', version: '0.0.1']]]
         } 
        }
       }
      }  