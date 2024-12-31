pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'Building the project'
                sh 'git --version'
                sh 'rm -rf wasp' 
                sh 'git clone https://github.com/Rahul-Kumar-Paswan/wasp.git'
                sh 'ls -l'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing the project'
                sshagent(credentials: ['aws-credentials']) {
                    sh '''
                    echo "Copying files to the EC2 instance"
                    scp -o StrictHostKeyChecking=no -r wasp/EmployeeInformation.war ec2-user@ec2-65-2-150-136.ap-south-1.compute.amazonaws.com:/home/ec2-user/source/
                    ssh -o StrictHostKeyChecking=no ec2-user@ec2-65-2-150-136.ap-south-1.compute.amazonaws.com <<EOF
                    echo "Files copied successfully. Listing the directory contents:"
                    ls -l /home/ec2-user/wasp
                    '''
                }
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying the project'
            }
        }
    }
}
