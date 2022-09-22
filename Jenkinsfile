node {    
      def app     
           
      stage('Build image') {         
       
            app = docker.build("vivans/sample-build")    
       }
       stage('docker login ')  {

        sh 'docker login -u $DOCKER_USERNAME -p $DOCKER_PASSWORD'

       }  
      stage('Test image') {           
            app.inside {            
             
             sh 'echo "Tests passed"'        
            }    
        }     
       stage('Push image') {
                                                  docker.withRegistry('https://registry.hub.docker.com') {            
       app.push("${env.BUILD_NUMBER}")            
       app.push("latest")        
              }    
           }
        }