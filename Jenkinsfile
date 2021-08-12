pipeline {
    
    agent any
    
    tools {
        maven 'Maven3'
        }
    stages {
        stage('Build') {
            
            steps {
                sh 'mvn -B -DskipTests clean package'
            }
        }
        
        stage('Build and tag docker image') {
            
            steps {
                sh 'cp /var/lib/jenkins/workspace/simple-hello-world-war-pipeline-docker/target/mkyong.war /var/lib/jenkins/docker/'
                sh 'docker build -t simple-hello-world-war:latest /var/lib/jenkins/docker/.'
                sh 'docker tag simple-hello-world-war astoiculescu/simple-hello-world-war:latest'
            }
        }
            
        stage('Publish image to dockerhub') {

            steps {
                withDockerRegistry([ credentialsId: "Docker-Hub", url: "" ]) {
                    sh  'docker push astoiculescu/simple-hello-world-war'
                }
            }
        }
        
        stage('Run docker container on production machine') {

            steps {
                sh 'docker -H ssh://vagrant@192.168.50.52 stop hello_world || true'
                sh 'docker -H ssh://vagrant@192.168.50.52 rm hello_world || true'
                sh 'docker -H ssh://vagrant@192.168.50.52 rmi astoiculescu/simple-hello-world-war:latest || true'
                withDockerRegistry([ credentialsId: "Docker-Hub", url: "" ]){
                    sh 'docker -H ssh://vagrant@192.168.50.52 run -d --name hello_world -p 8888:8080 astoiculescu/simple-hello-world-war'
                }
            }
        }
    }
}
