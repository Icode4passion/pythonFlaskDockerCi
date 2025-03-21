pipeline{
    agent any
    

    stages{
        stage("Clone reporsitory...."){
            steps{
                checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/Icode4passion/pythonFlaskDockerCi.git']])

            }
        }
        stage("Setting up Docker Compose file..."){
            steps{
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