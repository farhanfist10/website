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
                mkdir -p ${WORKSPACE}/deploy
                cp ${WORKSPACE}/index.html ${WORKSPACE}/deploy/
                cd ${WORKSPACE}/deploy
                ansible-playbook -i ${WORKSPACE}/slaves.txt ${WORKSPACE}/deploy.yaml
                '''
            }
        }
    }
}
