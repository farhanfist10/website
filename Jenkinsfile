pipeline {
    agent any

    stages {
        stage('Clone Website Repo') {
            steps {
                git 'https://github.com/farhanfist10/website.git'
            }
        }

        stage('Deploy to Slave via Ansible') {
            steps {
                sh '''
                cd /opt/deploy-website
                cp ${WORKSPACE}/index.html .
                ansible-playbook -i slaves.txt deploy.yaml
                '''
            }
        }
    }
}
