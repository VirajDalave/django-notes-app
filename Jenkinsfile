@Library("Shared") _
pipeline{
    
    agent { label "vinod" }
    
    stages{
        stage('Clean Workspace'){
            steps{
                cleanWs()
            }
        }
        stage('Code'){
            steps{
                script{
                    clone("https://github.com/VirajDalave/django-notes-app.git","main")
                }
            }
        }
        
        stage('Build'){
            steps{
                script{
                    docker_build("virajdalave","notes-app","latest")    
                }
                
            }
        }
        
        stage('Push to DockerHub'){
            steps{
                script{
                    docker_push("virajdalave","notes-app","latest")
                }
            }
        }
        
        stage('Deploy'){
            steps{
                echo "This will Deploy the code"
                sh "docker compose up -d"
            }
        }
    }
}
