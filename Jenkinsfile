pipeline {
    agent any
  stages {
        
        stage ('DeployToProduction') {
            when {
                branch 'master'
            }
            steps {
                input 'Deploy to Production'
                milestone(1)
                
                    script {
 
                        try {
                           sh "docker stop apache1"
                           sh "docker rm apache1"
                        } catch (err) {
                            echo: 'caught error: $err'
                        }
                        sh "docker run -dit --name apache1 -p 8082:80 -v /Users/coffeebeans/.jenkins/workspace/project-work/website.html:/usr/local/apache2/htdocs/ httpd:2.4"
                    
                }
            }
        }
    }
}




