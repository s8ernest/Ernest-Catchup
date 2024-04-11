pipeline {
    agent any
    parameters {
        string(name: 'BRANCH_NAME', defaultValue: 's8ernest', description: '')
    }
    stages {
        stage('Clone Repository') {
            steps {
                script {
                    // Clone the repository using SSH with private key and checkout the specific branch
                    git credentialsId: 'github-token',
                        url: 'https://github.com/s8ernest/Ernest-Catchup.git',
                        branch: "${params.BRANCH_NAME}"
                }
            }
        }
        // stage('Install Apache') {
        //     steps {
        //         script {
        //             sh """
        //                 sudo apt update
        //                 sudo apt install apache2 -y
        //                 sudo systemctl start apache2
        //                 sudo systemctl status apache2
        //                 sudo systemctl enable apache2
        //             """
        //         }
        //     }
        // }
        stage('Create a dir to deploy the code') {
            steps {
                script {
                    sh """
                        cd /var/www/html
                        sudo mkdir s8ernest || true
                    """ 
                }
            }
        }
        stage('Deploying the Code') {
            steps {
                script {
                    sh """
                        pwd
                        ls -l
                        sudo cp -r * /var/www/html/s8ernest
                    """ 
                }
            }
        }
    }
}
