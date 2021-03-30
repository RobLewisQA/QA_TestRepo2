pipeline{
        agent any
        stages{
            stage('Clone App'){
                sh "git init",
                sh "git clone https://gitlab.com/qacdevops/chaperootodo_client"
            }

            stage('Docker Install'){
                steps{
                    sh "sudo apt install curl",
                    sh "curl https://get.docker.com | sudo bash",
                    sh "sudo apt install -y curl jq",
                    sh 'sudo curl -L "https://github.com/docker/compose/releases/download/${version}/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose',
                    sh "sudo chmod +x /usr/local/bin/docker-compose"                    
                }
            }
            stage('Run App'){
                steps{
                    sh "sudo docker-compose pull && sudo -E DB_PASSWORD=${DB_PASSWORD}",
                    sh "sudo docker-compose up -d --build"
                }
            }
        }    
}
