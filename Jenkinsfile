pipeline {
    agent any
 stages {
  stage('Docker Build and Tag') {
           steps {
              
                sh 'docker build -t .' 
                  sh 'docker tag nodebuild vivans/nodebuild::latest'
                // sh 'docker tag nodebuild vivans/sample-build::$BUILD_NUMBER'
               
          }
        }
     
  stage('Publish image to Docker Hub') {
          
            steps {
        withDockerRegistry([ credentialsId: "dockerhub_id", url: "https://hub.docker.com/repository/docker/vivans/sample-build" ]) {
          sh  'docker push vivans/nodebuild::latest'
        //   sh  'docker push vivans/modebuild::$BUILD_NUMBER' 
        }
                  
          }
        }
     
//       stage('Run Docker container on Jenkins Agent') {
             
//             steps {
//                 sh "docker run -d -p 4030:80 nikhilnidhi/nginxtest"
 
//             }
//         }
//  stage('Run Docker container on remote hosts') {
             
//             steps {
//                 sh "docker -H ssh://jenkins@172.31.28.25 run -d -p 4001:80 nikhilnidhi/nginxtest"
 
//             }
//         }
    }
}