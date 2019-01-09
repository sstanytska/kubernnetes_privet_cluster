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
                ws("${workspace}/uat/kubernetes_cluster_private"){
                    sh "terraform init"
                }
            }
        }
        stage("Terraform Apply"){
            steps{
                ws("${workspace}/uat/kubernetes_cluster_private"){
                    sh "terraform ${action} -auto-approve"
                }
            }
        }
    }
}
