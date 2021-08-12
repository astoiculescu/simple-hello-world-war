pipeline {
    
    agent any
    
    tools {
            maven 'Maven3'
        }
    
    stages {
                
        stage('Build') {
            steps {
//                 sh 'mvn -B -DskipTests -Dv=${BUILD_NUMBER} clean package'
		sh 'mvn -B -DskipTests clean package'
            }
        }
	    
	    stage('Deploy') {
		    steps {
			sh 'scp /var/lib/jenkins/workspace/simple-hello-world-war-pipeline/target/mkyong.war vagrant@192.168.50.52:/usr/share/tomcat/apache-tomcat-8.5.69/webapps/'
// 			sh 'scp /var/lib/jenkins/workspace/simple-hello-world-war-pipeline/target/mkyong.${BUILD_NUMBER}.war vagrant@192.168.50.52:/usr/share/tomcat/apache-tomcat-8.5.69/webapps/'
// 			sh 'echo Current build number is  ${BUILD_NUMBER}'   
		    }
	    
	    }	    
    }
}
