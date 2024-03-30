pipeline {
    agent any 
    stages {
        stage('Clone the repo') {
            steps {
                echo 'clone the repo'
                sh 'rm -fr webapp24'
                sh 'git clone https://github.com/manvy-82/webapp24.git'
            }
            script 
            { stages 
                    // Define SSH credentials
                    def remoteServer = [
                        name: 'SSH_CREDENTIALS_ID', // 2b5387cd-0baf-497b-aa5c-8f363d129654
                        host: 'REMOTE_HOST',         // ec2-204-236-213-195.compute-1.amazonaws.com
                        user: 'REMOTE_USER',         // ec2-user
                        port: 22                      // SSH port (default is 22)
        }
        stage('push repo to remote host') {
            steps {
                echo 'connect to remote host and pull down the latest version'
                sh 'ssh -i ~/manvy_prp.pem ec2-user@204.236.213.195 sudo git -C /var/www/html pull'
            }
        }
        stage('Check website is up') {
            steps {
                echo 'Check website is up'
                sh 'curl -Is 204.236.213.195 | head -n 1'
            }
        }
    }
}
