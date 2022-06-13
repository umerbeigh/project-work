pipeline {
    agent any
  stages {
        
        stage ('DeployToStaging') {
            when {
                branch 'main'
            }
            steps {
                input 'Deploy to staging'
                
                    script {
 
                        try {
                           sh "docker stop apache1"
                           sh "docker rm apache1"
                        } catch (err) {
                            echo: 'caught error: $err'
                        }
                        sh "docker run -dit --name apache1 -p 8082:80 -v /Users/coffeebeans/.jenkins/workspace/handson2_main/:/usr/local/apache2/htdocs/ httpd:2.4"
                    
                }
            }
        }
      
      stage ('DeployToProduction') {
            when {
                branch 'main'
            }
            steps {
                input 'Deploy to Production'
                
                    script {
 
                        try {
                           sh "sudo docker stop apache4"
                           sh "sudo docker rm apache4"
                        } catch (err) {
                            echo: 'caught error: $err'
                        }
                        sh "sudo docker run -dit --name apache4 -p 8083:80 -v /Users/coffeebeans/.jenkins/workspace/handson2_main/:/usr/local/apache2/htdocs/ httpd:2.4"
                    
                }
            }
        }
      
      
    }
}




