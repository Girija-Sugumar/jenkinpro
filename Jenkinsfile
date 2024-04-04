@Library('shared_lib') _

pipeline{
    agent any
    stages{
        stage('git checkout'){
            steps{
                git branch: 'main', credentialsId: 'github_id', url: 'https://github.com/Girija-Sugumar/jenkinpro.git'
                
            }
        }
        tools {
          nodejs 'nodejs'
        }
        stage('npm package'){
            steps{
                npm()
            }
        }
        stage('pm2 module'){
            steps{
                pm2()
            }
        }
        stage('deploy node backend'){
            steps{
                script{
                    sh 'pm2 start index.js --name "nodebackend" -- --port 3000'
                }
            }
        }
    }
}
