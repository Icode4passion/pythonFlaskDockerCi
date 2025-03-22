pipeline{
    agent any
    environment {
        COMPOSE_FILE = "docker-compose.yml"
    }
    stages{
        stage("Clone reporsitory...."){
            steps{
                checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/Icode4passion/pythonFlaskDockerCi.git']])

            }
        }
        stage("Cleaning the container ..."){
            steps{
                sh '''
                    if [ "$(docker ps -aq -f name=flaskDcokerJenkinsApp)" ]; then
                        docker stop flaskDcokerJenkinsApp
                        docker rm flaskDcokerJenkinsApp
                    fi
                    '''

            }
        }
        stage("Setting up Docker Compose file..."){
            steps{
                sh 'docker system prune -f'
                sh "/usr/local/bin/docker-compose --version"
                sh "/usr/local/bin/docker-compose build"
                sh "/usr/local/bin/docker-compose up -d"
            }
        }
        stage("testing ..."){
            steps{
                sh "curl -f localhost:5000"
            }
        }
    }
}