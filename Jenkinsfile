pipeline {
  agent any

  stages {
    stage('Checkout') {
      steps {
        script {
          // Check out the repository containing your Terraform code
          checkout scm
        }
      }
    }
    stage('Terraform Init') {
      steps {
        script {
          // Change to the directory containing your Terraform code
          dir('/Users/saikaushikmanchala/Desktop/Integration ') {
            sh 'terraform init'
          }
        }
      }
    }
    stage('Terraform Plan') {
      steps {
        script {
          // Change to the directory containing your Terraform code
          dir('/Users/saikaushikmanchala/Desktop/Integration ') {
            sh 'terraform plan -out=tfplan'
          }
        }
      }
    }
    stage('Terraform Apply') {
      when {
        expression {
          currentBuild.resultIsBetterOrEqualTo('SUCCESS')
        }
      }
      steps {
        input 'Do you want to apply this Terraform plan?'
        script {
          // Change to the directory containing your Terraform code
          dir('/Users/saikaushikmanchala/Desktop/Integration ') {
            sh 'terraform apply tfplan'
          }
        }
      }
    }
}
}