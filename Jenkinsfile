pipeline {
    
    agent any
    
    tools {
            maven 'Maven3'
        }
    
    stages {
        
//         stage ('Clone') {
//             steps {
//                 script{
//                     git url: 'https://github.com/astoiculescu/simple-hello-world-war.git'
//                     sh "ls -lart ./*"
//                 } 
//             }
//         }
        
        stage('Build') {
            steps {
                sh 'mvn -B -DskipTests clean package'
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
	    stage('Copy .war artifact to production machine') {
		    steps {
			sh 'eval "$(ssh-agent)"'
			sh 'cd /home/vagrant/.ssh'
			sh 'ssh-add id_rsa'
// 			sh 'scp -v -o StrictHostKeyChecking=no /var/lib/jenkins/workspace/simple-hello-world-war-pipeline/target/mkyong.war vagrant@192.168.50.52:/usr/share/tomcat/apache-tomcat-8.5.69/webapps/'
			sh 'scp -i /home/vagrant/.ssh/id_rsa /var/lib/jenkins/workspace/simple-hello-world-war-pipeline/target/mkyong.war vagrant@192.168.50.52:/usr/share/tomcat/apache-tomcat-8.5.69/webapps/'
		    }
	    
	    }	    
    }
}
