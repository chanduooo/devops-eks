pipeline {
    agent any

    environment {
        AWS_ACCESS_KEY_ID     = credentials('aws_access_key_id')
        AWS_SECRET_ACCESS_KEY = credentials('aws_secret_access_key')
    }
    parameters {
          choice choices: ['apply', 'destroy'], name: 'action'
        }


    stages {
       stage('terraform init -input=false') {
            steps {
                sh 'terraform init'
            }
        }
      stage('terraform validate') {
            steps {
                sh 'terraform validate'
            }
        }
      stage('terraform plan') {
            steps {
                sh 'terraform plan'
            }
        }
      stage('terraform apply') {
            steps {
                sh 'terraform ${action} -auto-approve'
            }
        }
    }
}
