pipeline {
    agent any
  stages {
        
        stage ('DeployToProduction') {
            when {
                branch 'main'
            }
            steps {
                input 'Deploy to Production'
                
                    script {
 
                        try {
                           sh "docker stop apache1"
                           sh "docker rm apache1"
                        } catch (err) {
                            echo: 'caught error: $err'
                        }
                        sh "docker run -dit --name apache1 -p 8082:80 -v website.html:/usr/local/apache2/htdocs/ httpd:2.4"
                    
                }
            }
        }
    }
}




