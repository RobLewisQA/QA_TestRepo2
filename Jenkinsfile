pipeline{
        agent any
        stages{
            stage('Clone App'){
                sh "git init && git clone https://gitlab.com/qacdevops/chaperootodo_client"
            }

            stage('Docker Install'){
                steps{
                    sh "sudo apt install curl && curl https://get.docker.com | sudo bash && sudo apt install -y curl jq && sudo curl -L 'https://github.com/docker/compose/releases/download/${version}/docker-compose-$(uname -s)-$(uname -m)' -o /usr/local/bin/docker-compose && sudo chmod +x /usr/local/bin/docker-compose"                
                }
            }
            stage('Run App'){
                steps{
                    sh "sudo docker-compose pull && sudo -E DB_PASSWORD=${DB_PASSWORD} && sudo docker-compose up -d --build"
                }
            }
        }    
}
