pipeline {
    agent any

    stages {
        stage('Git Checkout') {
            steps {
                echo '******* Code checkout in progress *******'
                git branch: 'main', url: 'https://github.com/send2durai/infra-setup-for-project.git'
            }
        }
        stage ("Terraform Init"){
            steps{
                echo "******** Terraform Initialization ********"
                sh ("terraform init");
            }
        }
        stage("Terraform Action"){
            steps{
                echo "***** Terraform action from the parameter is --> ${action}"
                echo "***** Terraform action from the parameter is --> ${environment}"
                sh ("terraform ${action} --auto-approve");
            }
        }
    }
    post {
        always {
            echo "Going to send out an Job Notifications"
        }
        failure {
            slackSend channel: 'devops', message: 'Hey DevOps Team  #########  Jenkins Pipeline Job is Failure  #########'
        }
        success {
            slackSend channel: 'devops', message: 'Hey DevOps Team  #########  Jenkins Pipeline Job is Succeed  #########'
        }
    }
}
