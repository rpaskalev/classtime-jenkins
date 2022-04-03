pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
              sh '''
              echo "Planning infrastructure"
              cd terraform
              terraform init
              terraform plan
              '''
            }
        }
    stage('Deploy') {
        steps {
            sh '''
            echo "Deploying infrastructure..."
            cd terraform
            terraform apply -auto-approve
            '''
            }
        }
    }
    post {
      always {
        deleteDir()
      }
    }
}