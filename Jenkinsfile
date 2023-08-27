pipeline {
    agent any
    environment {
        AWS_ACCESS_KEY_ID = credentials('AWS secret access ID')
        AWS_SECRET_ACCESS_KEY = credentials('AWS sceret access key')
        DOCKER_CRED = credentials('Docker')
        Muthu = credentials('Muthur')
    }
    options {
        buildDiscarder logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '', daysToKeepStr: '', numToKeepStr: '2')
    }

    stages { 
        stage ('build') {
            steps {
                sh '''
                cd shoestop 
                ./build.sh 
                '''     
            }
        }

        stage ('push') {
            steps {
                sh '''
                cd Config/dockerpush
                ./push.sh
                '''
            }
        }

        stage ('server creation'){
            steps {
                sh '''
                cd Config/terraform
                ./infra.sh
                '''
            }
        }

        stage ('deployment') {
            steps {
                sh '''
                cd Config/ansible
                ./ansible.sh
                ansible-playbook -i inventory.txt --private-key=$Muthu ansible.yml
                '''
            }
        }
        
        stage ('loadbalancer') {
            steps {
                sh '''
                cd Config/loadbalancer
                ./lb.sh
                '''
            }
        }
    }
}
