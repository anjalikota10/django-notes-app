@Library("shared") _
pipeline {
    
    agent {label 'agent'}
    
    stages {
        
        stage ("Hello"){
            steps{
                script{
                    hello()
                }
            }
        }
        
        stage ("Code"){
            steps{
                script{
                  clone("https://github.com/anjalikota10/django-notes-app.git","main")
                }
            }
        }
        
        stage ("Build"){
            steps{
                script{
                docker_build("notes-app", "latest", "devops830")
                }

            }
        }
        
        stage ("Push Docker Image to dockerhub"){
            steps{
                script{
                    docker_push("notes-app","latest", "devops830")
                }
            }
        
            }
        
        stage ("Deploy"){
            steps{
                echo "This is deploying the code"
                sh 'docker compose up -d'
                
            }
        }
    }
}
