First Deploy eksCluster
then from awsCLI execute the following command
aws eks --region $(terraform output -raw region) update-kubeconfig --name $(terraform output -raw cluster_name)
then move on to deploy eksDeploy 
