pipeline{
    agent any
    parameters {
      string(defaultValue: "plan",  name: "action",  description: "Do you want plan or apply/destroy")
    }
    stages{
        stage("Pull repo"){
            steps{
                git 'https://github.com/sstanytska/terraform.git'
            }
        }
        stage("Terraform init"){
            steps{
                ws("${workspace}/uat/kubernetes_private_cluster"){
                    sh "terraform init"
                }
            }
        }
        stage("Terraform Plan"){
            steps{
                ws("${workspace}/uat/kubernetes_private_cluster"){
                    sh "terraform ${action}"
                }
            }
        }
    }
}
