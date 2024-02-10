First Deploy eksCluster

then from awsCLI execute the following command \n

aws eks --region $(terraform output -raw region) update-kubeconfig --name $(terraform output -raw cluster_name) \n

then move on to deploy eksDeploy 
