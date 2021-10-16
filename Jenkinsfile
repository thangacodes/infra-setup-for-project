pipeline {
    agent any

    stages {
        stage('Git Checkout') {
            steps {
                echo '******* Code checkout in progress *******'
                git branch: 'main', url: 'https://github.com/send2durai/infra-setup-for-project.git'
            }
        }
        stage ('Terraform Init'){
            steps{
                echo '******** Terraform Initialization ********'
                sh 'terraform init'
            }
        }
        stage('Terraform Action'){
            steps{
                echo '***** Terraform action from the parameter is --> ${action}'
                sh ('terraform ${action} --auto-approve');
            }
        }
    }
}