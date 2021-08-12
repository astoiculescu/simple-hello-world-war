pipeline {
    
    agent any
    
    tools {
            maven 'Maven3'
        }
    
    stages {
                
        stage('Build') {
            steps {
                sh 'mvn -B -DskipTests -Dv=${BUILD_NUMBER} clean package'
            }
        }
        // stage('Test') {
        //     steps {
        //         sh "chmod +x -R ${env.WORKSPACE}"
		      //  sh 'mvn test'
        //     }
        //     post {
        //         always {
        //             junit 'target/surefire-reports/*.xml'
        //         }
        //     }
        // }		
	    stage('Deploy') {
		    steps {
// 			sh 'scp -v -o StrictHostKeyChecking=no /var/lib/jenkins/workspace/simple-hello-world-war-pipeline/target/mkyong.war vagrant@192.168.50.52:/usr/share/tomcat/apache-tomcat-8.5.69/webapps/'
			    sh 'scp /var/lib/jenkins/workspace/simple-hello-world-war-pipeline/target/mkyong.${BUILD_NUMBER}.war vagrant@192.168.50.52:/usr/share/tomcat/apache-tomcat-8.5.69/webapps/'
			    sh 'echo Current build is ${BUILD_NUMBER}'   
		    }
	    
	    }	    
    }
}
