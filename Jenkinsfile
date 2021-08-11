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
	    
    }
}
