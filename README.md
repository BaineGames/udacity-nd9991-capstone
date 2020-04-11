# udacity-nd9991-capstone
Udacity Cloud DevOps Project - Capstone


Assuming aws cli is configured properly with an admin user

* run create-eks-role.sh to create the role needed to use eks services via cloudformation
* run create-eks-serv.sh to create the network needed for eks service to communicate via cloudformation
* initialize eks through aws web interface selecting the role, security group,  and vpcid from the output of the eks-role & eks-serv cloudformation stack
        NOTE: make sure you initialize the eks in console via the same user you are using for your aws cli. if you do it as a different user, you will not be able to connect to it.
* once cluster has finished creating - update your local kubeconfig to connect to the cluster
        I did this via aws cli using the command 'aws eks --region us-west-2 update-kubeconfig --name udacity-eks-cluster
* you can test if you can reach the cluster by using the command 'kubectl get svc'
* run create-eks-node-role.sh to create the role needed for worker nodes
* initalize worker node group through console to specification of your liking. be sure to use the proper role and subnets from the eks-node-role stack from cloudformation.
* Jenkinsfile pipeline handles the linting, building of the docker image, pushing image to registry, and then finally applying the app-deployment.yaml file to the kubernetes cluster.