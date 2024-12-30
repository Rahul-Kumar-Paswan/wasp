pipeline{
    agent any 
    stages{
        stage('Build'){
            steps{
                echo 'Building the project'
                sh 'git --version'
                sh 'git clone https://github.com/Rahul-Kumar-Paswan/wasp.git'
                sh 'ls -l'
            }
        }
        stage('Test'){
            steps{
                echo 'Testing the project'
            }
        }
        stage('Deploy'){
            steps{
                echo 'Deploying the project'
            }
        }
    }
}