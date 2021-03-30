pipeline{
        environment{
            DB_PASSWORD
        }
        agent any
        stages{
            stage('Run App'){
                steps{
                    sh "sudo docker-compose up -d --build"
                }
            }
        }    
}
