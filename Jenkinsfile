pipeline {
    agent any
    tools {
        terraform 'terraform'
    }
    stages {
        stage('Git init') {
            steps {
                git credentialsId: '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', url: 'https://github.com/123ASLIDDIN/jenkins.git'
            }
        }
        stage('Terraform init') {
            steps {
                sh 'terraform init -no-color'
            }
        }
        stage('Terraform plan') {
            steps {
                sh 'terraform plan -destroy -no-color'
            }
        }
        stage('Terraform Destroy') {
            input {
                message "Do you want to destroy deployment?"
            }
            steps {
                sh 'terraform destroy --auto-approve -no-color'
            }
        }
    }
}
