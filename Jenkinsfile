pipeline {
    agent any

   stages {
          stage('aws cred') {
            steps {
               withCredentials([[
                    $class: 'AmazonWebServicesCredentialsBinding',
                    credentialsId: "aws-cred",
                    accessKeyVariable: 'AWS_ACCESS_KEY_ID',
                    secretKeyVariable: 'AWS_SECRET_ACCESS_KEY']]) {
                }
            }
        }
    
        stage('init') {
            steps {
                sh 'terraform init'
            }
        }
        stage('validate') {
            steps {
                sh 'terraform validate'
          }
        }
         stage('plan') {
            steps {
                sh 'terraform plan'
         }
       }
         stage('apply') {
            steps {
                sh 'terraform apply --auto-approve'
        }
      }
        /*stage('destroy') {
            steps {
                sh 'terraform destroy --auto-approve'
        }
      }*/

}
}
