pipeline {
    agent any

    environment {
        WORK_DIR = '/opt/deploy-website'
    }

    stages {
        stage('Clone Website Repo') {
            steps {
                git branch: 'main', url: 'https://github.com/farhanfist10/website.git'
            }
        }

        stage('Deploy to Slave via Ansible') {
            steps {
                sh '''
                mkdir -p ${WORK_DIR}
                cp index.html ${WORK_DIR}/
                cd ${WORK_DIR}
                ansible-playbook -i slaves.txt deploy.yaml
                '''
            }
        }
    }
}
