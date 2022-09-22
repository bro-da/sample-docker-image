<<<<<<< HEAD
pipeline {
    agent any
 stages {
  stage('Docker Build and Tag') {
           steps {
              
                sh 'docker build -t nginxtest:latest .' 
                  sh 'docker tag nginxtest vivans/sample-build:latest'
                sh 'docker tag nginxtest vivans/sample-build:$BUILD_NUMBER'
               
          }
        }
     
  stage('Publish image to Docker Hub') {
          
            steps {
        withDockerRegistry([ credentialsId: "dockerHub", url: "" ]) {
          sh  'docker push vivans/sample-build:latest'
          sh  'docker push vivans/sample-build:$BUILD_NUMBER' 
        }
                  
          }
        }
     
//       stage('Run Docker container on Jenkins Agent') {
             
//             steps {
//                 sh "docker run -d -p 4030:80 vivans/sample-build:"
 
//             }
//         }
//  stage('Run Docker container on remote hosts') {
             
//             steps {
//                 sh "docker -H ssh://jenkins@172.31.28.25 run -d -p 4001:80 vivans/sample-build:"
 
//             }
        }
=======
pipeline { 
2
    environment { 
3
        registry = "https://hub.docker.com/repository/docker/vivans/sample-build" 
4
        registryCredential = 'dockerhub_id' 
5
        dockerImage = '' 
6
    }
7
    agent any 
8
    stages { 
// 9
//         stage('Cloning our Git') { 
// 10
//             steps { 
// 11
//                 git 'https://github.com/bro-da/sample-docker-image' 
// 12
//             }
// 13
//         } 
14
        stage('Building our image') { 
15
            steps { 
16
                script { 
17
                    dockerImage = docker.build registry + ":$BUILD_NUMBER" 
18
                }
19
            } 
20
        }
21
        stage('Deploy our image') { 
22
            steps { 
23
                script { 
24
                    docker.withRegistry( '', registryCredential ) { 
25
                        dockerImage.push() 
26
                    }
27
                } 
28
            }
29
        } 
30
        stage('Cleaning up') { 
31
            steps { 
32
                sh "docker rmi $registry:$BUILD_NUMBER" 
33
            }
34
        } 
35
>>>>>>> c62504fb96d62294e02bec6ebb2f45ee83113627
    }
36
}
