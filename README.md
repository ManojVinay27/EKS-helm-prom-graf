# EKS installations:





Install Kubectl:
----------------

curl -o kubectl https://s3.us-west-2.amazonaws.com/amazon-eks/1.22.6/2022-03-09/bin/linux/amd64/kubectl

chmod +x kubectl

cp kubectl /usr/bin

kubectl version --short --client

EKS install:
------------

curl --silent --location "https://github.com/weaveworks/eksctl/releases/latest/download/eksctl_$(uname -s)_amd64.tar.gz" | tar xz -C /tmp
sudo mv /tmp/eksctl /usr/bin
eksctl version

Cluster creation:
-----------------
eksctl create cluster --name=eksdemo \
                  --region=ap-south-1 \
                  --zones=ap-south-1a,ap-south-1b \
                  --without-nodegroup 


Add IAM providers:
-----------------

eksctl utils associate-iam-oidc-provider \
    --region ap-south-1 \
    --cluster eksdemo \
    --approve

Create cluster node group:
-------------------------


eksctl create nodegroup --cluster=eksdemo \
                   --region=ap-south-1 \
                   --name=eksdemo-ng-public \
                   --node-type=t2.medium \
                   --nodes=2 \
                   --nodes-min=2 \
                   --nodes-max=4 \
                   --node-volume-size=10 \
                   --ssh-access \
                   --ssh-public-key=new \     ####Replace this
                   --managed \
                   --asg-access \
                   --external-dns-access \
                   --full-ecr-access \
                   --appmesh-access \
                   --alb-ingress-access	

                   
Delete node group:
------------------

eksctl delete nodegroup --cluster=eksdemo \
                   --region=ap-south-1 \
	          			   --name=eksdemo-ng-public	


delete cluster
--------------

eksctl delete cluster --name=eksdemo \
                  --region=ap-south-1
