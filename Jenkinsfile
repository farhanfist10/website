pipeline {
    agent any

    stages {
        stage('Clone Repo') {
            steps {
                git url: 'https://github.com/farhanfist10/website.git', branch: 'main'
            }
        }

        stage('Deploy to Slaves') {
            steps {
                script {
                    def pemKeyPath = "/home/ec2-user/pro.pem"
                    def slaves = ["172.31.89.190", "172.31.95.146"]
                    for (slave in slaves) {
                        sh """
                            echo "Deploying to ${slave}"
                            scp -i ${pemKeyPath} -o StrictHostKeyChecking=no index.html ec2-user@${slave}:/var/www/html/index.html
                        """
                    }
                }
            }
        }
    }
}
